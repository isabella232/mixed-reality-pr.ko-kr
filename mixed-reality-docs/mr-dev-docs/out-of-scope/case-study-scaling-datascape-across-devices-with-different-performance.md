---
title: 사례 연구 - 성능이 다른 디바이스에서 Datascape 크기 조정
description: 이 사례 연구에서는 Microsoft 개발자가 다양한 성능 기능을 갖춘 디바이스 간에 매력적인 환경을 제공하기 위해 Datascape 앱을 최적화한 방법에 대한 인사이트를 제공합니다.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 몰입형 헤드셋, 성능 최적화, VR, 사례 연구
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195798"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>사례 연구 - 성능이 다른 디바이스에서 Datascape 크기 조정

Datascape는 Microsoft에서 내부적으로 개발된 Windows Mixed Reality 애플리케이션으로, 지형 데이터를 기반으로 날씨 데이터를 표시하는 데 집중했습니다. 애플리케이션은 사용자를 홀로그램 데이터 시각화로 둘러쌓아 혼합 현실에서 데이터를 검색하여 얻을 수 있는 고유한 인사이트를 탐색합니다.

Datascape의 경우 Microsoft HoloLens, 몰입형 헤드셋 Windows Mixed Reality, 저전력 PC에서 고성능 GPU가 있는 최신 PC까지 다양한 하드웨어 기능을 갖춘 다양한 플랫폼을 대상으로 지정하려고 했습니다. 주요 과제는 높은 프레임 속도로 실행되는 동안 그래픽 기능이 매우 다른 디바이스에서 시각적으로 매력적인 문제의 장면을 렌더링하는 것이었습니다.

이 사례 연구에서는 GPU를 많이 사용하는 시스템 중 일부를 만드는 데 사용되는 프로세스와 기술을 안내하고, 발생한 문제와 이를 어떻게 극복했는지 설명합니다.

## <a name="transparency-and-overdraw"></a>투명도 및 초과 그리기

투명성은 GPU에서 비용이 많이 들 수 있기 때문에 주요 렌더링은 투명성을 처리하는 데 어려움을 겪습니다.

깊이 버퍼에 쓰는 동안 단색 기하 도형을 앞으로 렌더링하여 해당 픽셀 뒤에 있는 모든 미래 픽셀이 삭제되지 않도록 할 수 있습니다. 이렇게 하면 숨겨진 픽셀이 픽셀 셰이더를 실행하지 못하여 프로세스 속도가 크게 빨라집니다. 기하 도형이 최적으로 정렬되면 화면의 각 픽셀이 한 번만 그려집니다.

투명 기하 도형을 다시 전면으로 정렬해야 하며 픽셀 셰이더의 출력을 화면의 현재 픽셀과 혼합해야 합니다. 이로 인해 화면의 각 픽셀이 프레임당 여러 번 그려질 수 있으며 이를 overdraw라고 합니다.

HoloLens 및 일반 PC의 경우 화면이 몇 번만 채워져 투명 렌더링에 문제가 있습니다.

## <a name="introduction-to-datascape-scene-components"></a>데이터 스케이프 장면 구성 요소 소개

장면에는 세 가지 주요 구성 요소가 있었습니다. **UI, 지도** 및 **날씨 입니다.** 날씨 효과에는 가져올 수 있는 모든 GPU 시간이 필요하다는 것을 초기에 알았으므로, 오버드로를 줄이는 방식으로 UI 및 지형을 의도적으로 디자인했습니다.

UI가 생성하는 초과 그리기의 양을 최소화하기 위해 UI를 여러 번 다시 작업했습니다. 광선 단추 및 지도 개요와 같은 구성 요소에 대해 서로 위에 투명 아트를 오버레이하는 대신 더 복잡한 기하 도형의 측면에서 오류했습니다.

맵의 경우 그림자 및 복잡한 조명과 같은 표준 Unity 기능을 제거하는 사용자 지정 셰이더를 사용하여 간단한 단일 태양 조명 모델 및 사용자 지정 색 계산으로 대체했습니다. 이렇게 하면 간단한 픽셀 셰이더가 생성되고 GPU 주기가 확보됩니다.

UI와 맵을 모두 하드웨어에 따라 변경할 필요가 없는 예산으로 렌더링하도록 관리했습니다. 그러나 날씨 시각화, 특히 클라우드 렌더링은 더 어려운 과제로 입증되었습니다.

## <a name="background-on-cloud-data"></a>클라우드 데이터에 대한 배경 지식

클라우드 데이터는 NOAA 서버(에서 https://nomads.ncep.noaa.gov/) 다운로드되었으며, 각각 클라우드의 위쪽 및 아래쪽 높이와 그리드의 각 셀에 대한 클라우드 밀도를 가진 세 개의 고유한 2D 계층으로 다운로드되었습니다. 데이터는 GPU에서 쉽게 액세스할 수 있도록 각 구성 요소가 질감의 빨간색, 녹색 및 파란색 구성 요소에 저장된 클라우드 정보 질감으로 처리되었습니다.

## <a name="geometry-clouds"></a>기하 도형 클라우드

저전력 머신이 클라우드를 렌더링할 수 있도록 하기 위해 단색 기하 도형을 사용하여 오버드로를 최소화하는 접근 방식을 시작하기로 결정했습니다.

먼저 꼭짓점당 클라우드 정보 질감의 반지름을 사용하여 각 계층에 대해 단색 높이 맵 메시를 생성하여 모양을 생성하여 클라우드를 생성하려고 했습니다. 기하 도형 셰이더를 사용하여 클라우드의 위쪽과 아래쪽 모두에서 꼭짓점을 생성하여 견고한 클라우드 셰이프를 생성했습니다. 질감의 밀도 값을 사용하여 더 조밀한 클라우드에 대해 더 어두운 색으로 클라우드에 색을 지정했습니다.

**꼭짓점을 만들기 위한 셰이더:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

실제 데이터에 대한 자세한 정보를 얻기 위해 작은 노이즈 패턴을 도입했습니다. 둥근 클라우드 가장자리를 생성하기 위해 보간된 반경 값이 임계값에 도달하여 0에 가까운 값을 삭제할 때 픽셀 셰이더의 픽셀을 잘렸습니다.

![기하 도형 클라우드](images/datascape-geometry-clouds-700px.jpg)

클라우드는 단색 기하 도형이므로 지형 앞에 렌더링하여 프레임 속도를 더욱 향상시키기 위해 아래에 비용이 많이 드는 지도 픽셀을 숨길 수 있습니다. 이 솔루션은 단색 기하 도형 렌더링 접근 방식 때문에 HoloLens 뿐만 아니라 최소 사양에서 고급 그래픽 카드까지 모든 그래픽 카드에서 잘 실행되었습니다.

## <a name="solid-particle-clouds"></a>반도체 클라우드

이제 클라우드 데이터의 적절한 표현을 생성하는 백업 솔루션이 있었지만 "wow" 요소에서는 약간 부족했으며, 고성능 머신에 원하는 볼륨 느낌을 전달하지 못했습니다.

다음 단계에서는 약 100,000개의 입자로 클라우드를 표시하여 더 유기적이고 볼륨이 많은 모양을 생성하는 것이었습니다.

파티클이 단색으로 유지되고 앞에서 뒤로 정렬하는 경우에도 이전에 렌더링된 파티클 뒤의 픽셀 깊이 버퍼 선별을 통해 오버드로를 줄일 수 있습니다. 또한 파티클 기반 솔루션을 사용하면 다른 하드웨어를 대상으로 하는 데 사용되는 파티클의 양을 변경할 수 있습니다. 그러나 모든 픽셀을 깊이 테스트해야 하므로 약간의 추가 오버헤드가 발생합니다.

먼저 시작 시 환경의 중심점 주위에 파티클 위치를 만들었습니다. 중심을 중심으로 더 조밀하게 파티클을 분산시켰고 멀리 떨어진 곳에 분산했습니다. 가장 가까운 파티클이 먼저 렌더링되도록 모든 파티클을 가운데에서 뒤로 미리 정렬했습니다.

컴퓨팅 셰이더에서는 클라우드 정보 질감을 샘플링하여 각 파티클을 올바른 높이로 배치하고 밀도에 따라 색을 지정합니다.

*DrawProcedural을* 사용하여 파티클 데이터를 GPU에 항상 유지할 수 있도록 파티클당 쿼드를 렌더링했습니다.

각 파티클에는 높이와 반경이 모두 포함되어 있습니다. 높이는 클라우드 정보 질감에서 샘플링된 클라우드 데이터를 기반으로 하며, 반경은 가장 가까운 인접 환경까지의 수평 거리를 저장하기 위해 계산되는 초기 분포를 기반으로 합니다. 쿼드는 사용자가 가로로 볼 때 높이가 표시되고 사용자가 위쪽에서 볼 때 인접 영역이 덮어지도록 높이에 따라 기울어져 있는 방향을 지정하는 데 이 데이터를 사용합니다.

![파티클 모양](images/particle-shape-700px.png)

**분포를 보여주는 셰이더 코드:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

파티클을 전면에서 뒤로 정렬하고 투명 픽셀을 잘라내기 위해 단색 셰이더를 사용했으므로 이 기술은 놀라운 양의 파티클을 처리하여 저전력 컴퓨터에서도 비용이 많이 드는 오버 그리기를 방지합니다.

## <a name="transparent-particle-clouds"></a>투명 파티클 클라우드

단색 입자는 클라우드 모양에 유기적인 느낌을 제공했지만 여전히 클라우드의 견고성을 판매하기 위해 필요한 것이 필요했습니다. 투명도를 도입할 수 있는 고급 그래픽 카드에 대한 사용자 지정 솔루션을 시도하기로 결정했습니다.

이를 위해 파티클의 초기 정렬 순서를 전환하고 질감 알파를 사용하도록 셰이더를 변경했습니다.

![흐리고 흐리고 있는 클라우드](images/fluffy-clouds-700px.jpg)

보기에는 좋지만 화면에 각 픽셀을 수백 번 렌더링하게 되므로 가장 까다로운 머신에 대해서도 너무 많은 것으로 입증되었습니다.

## <a name="render-off-screen-with-lower-resolution"></a>낮은 해상도로 화면 끄기 렌더링

클라우드에서 렌더링되는 픽셀 수를 줄이기 위해 4분 해상도 버퍼에서 렌더링하고(화면에 비해) 모든 파티클을 그린 후 최종 결과를 화면으로 다시 확장하기 시작했습니다. 이로써 속도는 약 4배까지 빨라졌지만 몇 가지 주의 사항이 있습니다.

**화면 끄기 렌더링을 위한 코드:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

첫째, 화면 끄기 버퍼로 렌더링할 때 주 장면에서 모든 깊이 정보가 손실되어 산 위에 있는 획 렌더링 뒤에 파티클이 생성됩니다.

둘째, 버퍼를 확장하면 해상도 변경이 두드러진 클라우드 가장자리에 아티팩트도 도입되었습니다. 다음 두 섹션에서는 이러한 문제를 어떻게 해결했는지에 대해 논의합니다.

## <a name="particle-depth-buffer"></a>파티클 깊이 버퍼

산 또는 개체가 그 뒤의 입자를 덮을 수 있는 세계 기하 도형과 파티클이 공존하도록 하기 위해 화면 끄기 버퍼에 주 장면의 기하 도형을 포함하는 깊이 버퍼를 채웁니다. 이러한 깊이 버퍼를 생성하기 위해 두 번째 카메라를 만들어 장면의 단색 기하 도형과 깊이만 렌더링했습니다.

그런 다음, 클라우드의 픽셀 셰이더에서 새 질감을 사용하여 픽셀을 폐색했습니다. 동일한 질감을 사용하여 클라우드 픽셀 뒤의 기하 도형까지의 거리를 계산했습니다. 이제 해당 거리를 사용하여 픽셀의 알파에 적용하면 지형에 가까워지면서 클라우드가 흐리게 표시되어 입자와 지형이 충족되는 하드 절단이 제거됩니다.

![지형으로 혼합된 클라우드](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>가장자리 선명하게

확장된 클라우드는 파티클의 중심이나 겹치는 위치의 일반 크기 클라우드와 거의 동일해 보이지만 클라우드 가장자리에 일부 아티팩트만 표시되었습니다. 그렇지 않으면 선명한 가장자리가 흐리게 표시되고 카메라를 이동할 때 별칭 효과가 도입되었습니다.

화면 끄기 버퍼에서 간단한 셰이더를 실행하여 큰 대비 변경이 발생한 위치를 확인하여 이 문제를 해결했습니다(1). 큰 변경 내용이 있는 픽셀을 새 스텐실 버퍼에 넣습니다(2). 그런 다음, 스텐실 버퍼를 사용하여 화면 외부 버퍼를 화면에 다시 적용할 때 이러한 고대비 영역을 마스킹하여 클라우드 안팎에 구멍이 발생합니다(3).

그런 다음, 모든 파티클을 전체 화면 모드로 다시 렌더링했지만 이번에는 스텐실 버퍼를 사용하여 가장자리를 제외한 모든 것을 마스킹하여 최소한의 픽셀 세트가 닿습니다(4). 파티클에 대한 명령 버퍼가 이미 만들어졌으므로 새 카메라에 다시 렌더링해야 했습니다.

![클라우드 에지 렌더링 진행](images/cloud-steps-1-4-700px.jpg)

최종 결과는 클라우드의 저렴한 중심 섹션이 있는 예리한 가장자리였습니다.

전체 화면에서 모든 파티클을 렌더링하는 것보다 훨씬 더 빠르지만 스텐실 버퍼에 대해 픽셀을 테스트하는 데 비용이 계속 들기 때문에 여전히 많은 양의 오버드로 비용이 수반됩니다.

## <a name="culling-particles"></a>파티클 제거

풍향을 위해 컴퓨팅 셰이더에 긴 삼각형 스트립을 생성하여 전 세계에 많은 풍속을 만들었습니다. 폭주 줄무늬가 생성되어 풍속이 많이 발생하지는 않았지만, 수백 만 개의 꼭짓점이 생성되어 꼭짓점 셰이더에 대한 부하가 많이 발생했습니다.

컴퓨팅 셰이더에 추가 버퍼를 도입하여 그릴 풍력 스트립의 하위 집합을 공급했습니다. 컴퓨팅 셰이더에서 몇 가지 간단한 보기 frustum 엄선 논리를 사용하여 스트립이 카메라 보기 외부에 있는지 확인하고 푸시 버퍼에 추가되지 않도록 방지할 수 있습니다. 이렇게 하면 스트립의 양이 크게 줄어들어 GPU에서 필요한 일부 주기가 확보됩니다.

**추가 버퍼를 보여주는 코드:**

*컴퓨팅 셰이더:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C# 코드:*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

클라우드 파티클에서 동일한 기술을 사용하려고 했습니다. 여기서는 컴퓨팅 셰이더에서 해당 입자를 선별하고 표시되는 파티클만 렌더링하도록 푸시했습니다. 가장 큰 병목 현상은 꼭짓점을 계산하는 비용이 아니라 화면에 렌더링된 픽셀 크기이기 때문에 이 기술은 실제로 GPU에 많은 비용을 절감하지 못했습니다.

이 기술의 다른 문제는 파티클을 계산하는 병렬화된 특성으로 인해 추가 버퍼가 임의 순서로 채워져 정렬된 파티클이 정렬되지 않아 클라우드 파티클이 깜박이기 때문입니다.

푸시 버퍼를 정렬하는 기술이 있지만, 파티클 선별에서 얻은 성능 향상의 제한된 양은 추가 정렬로 오프셋될 수 있으므로 이 최적화를 추진하지 않기로 결정했습니다.

## <a name="adaptive-rendering"></a>적응형 렌더링

흐리기 또는 명확한 보기와 같은 다양한 렌더링 조건이 있는 앱에서 안정적인 프레임 속도 보장을 위해 앱에 적응형 렌더링을 도입했습니다.

적응형 렌더링의 첫 번째 단계는 GPU를 측정하는 것입니다. 이 작업을 위해 렌더링된 프레임의 시작과 끝에 있는 GPU 명령 버퍼에 사용자 지정 코드를 삽입하고 왼쪽 및 오른쪽 눈 화면 시간을 모두 캡처했습니다.

렌더링에 소요된 시간을 측정하고 원하는 새로 고침 빈도와 비교하여 프레임을 삭제하는 데 얼마나 근접했는지 알 수 있었습니다.

프레임 삭제에 가까워지면 렌더링을 더 빠르게 조정할 수 있습니다. 조정하는 간단한 방법 중 하나는 화면의 뷰포트 크기를 변경하여 렌더링할 픽셀을 줄이는 것입니다.

*UnityEngine.XR.XRSettings.renderViewportScale을* 사용하여 시스템은 대상 뷰포트를 축소하고 화면에 맞게 결과를 자동으로 다시 늘립니다. 세계 기하 도형에서 눈금의 작은 변경은 거의 눈에 띄지 않으며, 배율 0.7의 배율에는 렌더링할 픽셀의 양이 절반이어야 합니다.

![70% 배율, 픽셀의 절반](images/datascape-scaling-700px.jpg)

프레임을 삭제하려고 한다는 것을 감지하면 고정된 수만큼 배율을 낮추고, 충분히 빠르게 다시 실행할 때 다시 늘립니다.

시작 시 하드웨어의 그래픽 기능을 기반으로 사용할 클라우드 기술을 결정했지만, 시스템이 오랫동안 낮은 해상도로 유지되지 않도록 GPU 측정값의 데이터를 기반으로 할 수 있지만 Datascape에서 살펴볼 시간이 없었습니다.

## <a name="final-thoughts"></a>맺음말

다양한 하드웨어를 대상으로 지정하는 것은 어려운 일이며 몇 가지 계획이 필요합니다.

문제 공간에 익숙해지고 모든 컴퓨터에서 실행되는 백업 솔루션을 개발하려면 저전력 컴퓨터를 대상으로 지정하는 것이 좋습니다. 픽셀이 가장 귀중한 리소스가 되므로 채우기 속도를 염두에 두고 솔루션을 디자인합니다. 투명도를 통해 단색 기하 도형을 대상으로 지정합니다.

백업 솔루션을 사용하면 고급 머신에 대해 더 복잡한 계층화를 시작하거나 백업 솔루션의 해상도를 향상시킬 수 있습니다.

최악의 시나리오에 맞게 디자인하고, 많은 상황에 적응형 렌더링을 사용하는 것이 좋습니다.

## <a name="about-the-authors"></a>작성자 정보

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>RobertRese</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>추가 정보
* [Mixed Reality 성능 이해](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity용 성능 권장 사항](../develop/unity/performance-recommendations-for-unity.md)

 

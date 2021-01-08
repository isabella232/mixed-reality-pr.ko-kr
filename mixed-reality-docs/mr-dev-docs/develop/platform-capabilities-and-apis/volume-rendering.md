---
title: 볼륨 렌더링
description: Windows Mixed Reality에서 불투명도 및 색을 사용 하 여 다양 한 대규모 이미지를 효율적으로 렌더링 하는 방법에 대해 알아봅니다.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 대규모 이미지, 볼륨 렌더링, 성능, 혼합 현실
ms.openlocfilehash: 2a76be80d786aea0c8bc1bd364155fa37d37e151
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008783"
---
# <a name="volume-rendering"></a><span data-ttu-id="774aa-104">볼륨 렌더링</span><span class="sxs-lookup"><span data-stu-id="774aa-104">Volume rendering</span></span>

<span data-ttu-id="774aa-105">의료 MRI 또는 엔지니어링 볼륨의 경우 [위키백과에서 볼륨 렌더링](https://en.wikipedia.org/wiki/Volume_rendering)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="774aa-105">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="774aa-106">이러한 ' 대규모 images '에는 [다각형 메시](https://en.wikipedia.org/wiki/Polygon_mesh)와 같이 표면으로 쉽게 표현 될 수 없는 볼륨 전체에서 불투명도 및 색을 사용 하는 다양 한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-106">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="774aa-107">성능 향상을 위한 주요 솔루션</span><span class="sxs-lookup"><span data-stu-id="774aa-107">Key solutions to improve performance</span></span>
1. <span data-ttu-id="774aa-108">잘못 됨: Naive 접근 방식: 전체 볼륨을 표시 합니다. 일반적으로 너무 느리게 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-108">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="774aa-109">양호: 절삭 평면: 볼륨의 단일 조각만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-109">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="774aa-110">양호: 하위 볼륨 잘라내기: 볼륨의 일부 레이어만 표시</span><span class="sxs-lookup"><span data-stu-id="774aa-110">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="774aa-111">양호: 볼륨 렌더링의 해상도를 낮춥니다 (' 혼합 해상도 장면 렌더링 ' 참조).</span><span class="sxs-lookup"><span data-stu-id="774aa-111">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="774aa-112">응용 프로그램에서 특정 프레임의 화면으로 전송 될 수 있는 정보에는 총 메모리 대역폭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-112">There's only a certain amount of information that can be transferred from the application to the screen in any particular frame, which is the total memory bandwidth.</span></span> <span data-ttu-id="774aa-113">또한 프레젠테이션을 위해 데이터를 변환 하는 데 필요한 모든 처리 (또는 ' 음영 ')에는 시간이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-113">Also, any processing (or 'shading') required to transform that data for presentation requires time.</span></span> <span data-ttu-id="774aa-114">볼륨 렌더링을 수행할 때 기본적인 고려 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-114">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="774aa-115">Screen-Width \* Screen-Height \* Screen-Count \* 볼륨-계층-픽셀 = 전체-볼륨 샘플-프레임당 샘플</span><span class="sxs-lookup"><span data-stu-id="774aa-115">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="774aa-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (전체 res 볼륨: 샘플이 너무 많음)</span><span class="sxs-lookup"><span data-stu-id="774aa-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="774aa-117">1028 \* 720 \* 2 \* 1 = 1480320 (전체의 0.3%) (씬 조각: 픽셀당 1 개 샘플, 부드럽게 실행)</span><span class="sxs-lookup"><span data-stu-id="774aa-117">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="774aa-118">1028 \* 720 \* 2 \* 10 = 14803200 (전체의 3.9%) (subvolume slice: 픽셀당 10 개 샘플, 매우 매끄럽게 실행, 3d가 표시 됨)</span><span class="sxs-lookup"><span data-stu-id="774aa-118">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (subvolume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="774aa-119">200 \* 200 \* 2 \* 256 = 2048만 (전체의 5%) (더 낮은 res 볼륨: 더 적은 픽셀, 전체 볼륨, 3d로 보이지만 약간 흐린)</span><span class="sxs-lookup"><span data-stu-id="774aa-119">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blurry)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="774aa-120">3D 질감 표시</span><span class="sxs-lookup"><span data-stu-id="774aa-120">Representing 3D Textures</span></span>

<span data-ttu-id="774aa-121">CPU:</span><span class="sxs-lookup"><span data-stu-id="774aa-121">On the CPU:</span></span>

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

<span data-ttu-id="774aa-122">GPU:</span><span class="sxs-lookup"><span data-stu-id="774aa-122">On the GPU:</span></span>

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a><span data-ttu-id="774aa-123">음영 및 그라데이션</span><span class="sxs-lookup"><span data-stu-id="774aa-123">Shading and Gradients</span></span>

<span data-ttu-id="774aa-124">유용한 시각화를 위해 MRI와 같은 볼륨을 음영 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-124">How to shade a volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="774aa-125">기본 방법은 강도를 보려는 ' 강도 창 ' (최소 및 최대)을 보유 하는 것이 고, 해당 공간으로 크기를 조정 하 여 검정색과 백색 강도를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-125">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="774aa-126">그러면 ' 색 램프 '가 해당 범위 내에 있는 값에 적용 되 고 질감으로 저장 될 수 있으므로 강도 스펙트럼의 각 부분이 서로 다른 색으로 음영 처리 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-126">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="774aa-127">대부분의 응용 프로그램에서는 기본 강도 값과 ' 조각화 인덱스 '를 모두 볼륨에 저장 합니다. 스킨 및 뼈와 같은 여러 부분을 분할 하려면 이러한 세그먼트가 전용 도구의 전문가에 의해 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-127">In many of our applications, we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone; these segments are created by experts in dedicated tools).</span></span> <span data-ttu-id="774aa-128">위의 방법으로 결합 하 여 다른 색 이나 각 세그먼트 인덱스 마다 다른 색 램프를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-128">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="774aa-129">셰이더의 볼륨 조각화</span><span class="sxs-lookup"><span data-stu-id="774aa-129">Volume Slicing in a Shader</span></span>

<span data-ttu-id="774aa-130">첫 번째 단계는 볼륨을 이동 하 고, ' 조각화 ' 하 고, 각 지점에서 값을 검색 하는 방법을 "조각화 평면"을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-130">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="774aa-131">여기서는 볼륨이 세계 공간에 있는 위치를 나타내는 ' VolumeSpace ' 큐브가 있다고 가정 합니다 .이는 요소를 배치 하기 위한 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-131">This assumes that there's a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="774aa-132">셰이더에서 볼륨 추적</span><span class="sxs-lookup"><span data-stu-id="774aa-132">Volume Tracing in Shaders</span></span>

<span data-ttu-id="774aa-133">GPU를 사용 하 여 하위 볼륨 추적을 수행 하는 방법 (몇 가지 voxels를 보여 주는 후 데이터의 계층을 뒤로 이동).</span><span class="sxs-lookup"><span data-stu-id="774aa-133">How to use the GPU to do subvolume tracing (walks a few voxels deep, then layers on the data from back to front):</span></span>

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a><span data-ttu-id="774aa-134">전체 볼륨 렌더링</span><span class="sxs-lookup"><span data-stu-id="774aa-134">Whole Volume Rendering</span></span>

<span data-ttu-id="774aa-135">위의 하위 볼륨 코드를 수정 하면 다음을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-135">Modifying the subvolume code above, we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="774aa-136">혼합 해상도 장면 렌더링</span><span class="sxs-lookup"><span data-stu-id="774aa-136">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="774aa-137">낮은 해상도로 장면의 일부를 렌더링 하 고 다시 배치 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-137">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="774aa-138">각 프레임을 업데이트 하는 각 눈에 따라 하나씩, 두 개의 오프 스크린 카메라를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-138">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="774aa-139">카메라에서 렌더링 하는 두 가지 저해상도 렌더링 대상 (즉, 각각 200 x 200)을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-139">Setup two low-resolution render targets (that is, 200x200 each) that the cameras render into</span></span>
3. <span data-ttu-id="774aa-140">사용자 앞으로 이동 하는 쿼드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-140">Set up a quad that moves in front of the user</span></span>

<span data-ttu-id="774aa-141">각 프레임:</span><span class="sxs-lookup"><span data-stu-id="774aa-141">Each Frame:</span></span>
1. <span data-ttu-id="774aa-142">저해상도 (볼륨 데이터, 비용이 많이 드는 셰이더 등)에서 각 눈에 대 한 렌더링 대상을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-142">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, and so on)</span></span>
2. <span data-ttu-id="774aa-143">보통 전체 해상도 (메시, UI 등)로 장면 그리기</span><span class="sxs-lookup"><span data-stu-id="774aa-143">Draw the scene normally as full resolution (meshes, UI, and so on)</span></span>
3. <span data-ttu-id="774aa-144">장면에 대해 사용자 앞에 쿼드를 그리고 해당 하는 하위 범위의 렌더링을 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="774aa-144">Draw a quad in front of the user, over the scene, and project the low-res renders onto that</span></span>
4. <span data-ttu-id="774aa-145">결과: 해상도가 낮거나 고밀도 볼륨 데이터로 전체 해상도 요소를 시각적으로 결합</span><span class="sxs-lookup"><span data-stu-id="774aa-145">Result: visual combination of full-resolution elements with low-resolution but high-density volume data</span></span>

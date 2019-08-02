---
title: 부동 소수점 숫자 형식 - C# 참조
description: 기본 제공 C# 부동 소수점 형식의 개요
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236053"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="1ca53-103">부동 소수점 숫자 형식(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="1ca53-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="1ca53-104">**부동 소수점 형식**은 **단순 형식**의 하위 집합이며 [*리터럴*](#floating-point-literals)을 사용하여 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="1ca53-105">모든 부동 소수점 형식도 값 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-105">All floating-point types are also value types.</span></span> <span data-ttu-id="1ca53-106">모든 부동 소수점 숫자 형식은 [산술](../operators/arithmetic-operators.md), [비교 및 같음](../operators/equality-operators.md) 연산자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="1ca53-107">부동 소수점 형식의 특성</span><span class="sxs-lookup"><span data-stu-id="1ca53-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="1ca53-108">C#은 다음과 같은 미리 정의된 부동 소수점 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="1ca53-109">C# 형식/키워드</span><span class="sxs-lookup"><span data-stu-id="1ca53-109">C# type/keyword</span></span>|<span data-ttu-id="1ca53-110">근사 범위</span><span class="sxs-lookup"><span data-stu-id="1ca53-110">Approximate range</span></span>|<span data-ttu-id="1ca53-111">전체 자릿수</span><span class="sxs-lookup"><span data-stu-id="1ca53-111">Precision</span></span>|<span data-ttu-id="1ca53-112">.NET 형식</span><span class="sxs-lookup"><span data-stu-id="1ca53-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="1ca53-113">±1.5 x 10<sup>−45</sup> ~ ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="1ca53-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="1ca53-114">~6-9개 자릿수</span><span class="sxs-lookup"><span data-stu-id="1ca53-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="1ca53-115">±5.0 × 10<sup>−324</sup> ~ ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="1ca53-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="1ca53-116">~15-17개 자릿수</span><span class="sxs-lookup"><span data-stu-id="1ca53-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="1ca53-117">±1.0 x 10<sup>-28</sup> ~ ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="1ca53-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="1ca53-118">28-29개의 자릿수</span><span class="sxs-lookup"><span data-stu-id="1ca53-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="1ca53-119">이전 표에서 맨 왼쪽 열의 각 C# 형식 키워드는 해당하는 .NET 형식의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="1ca53-120">서로 교환하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-120">They are interchangeable.</span></span> <span data-ttu-id="1ca53-121">예를 들어 다음 선언은 동일한 형식의 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="1ca53-122">각 부동 소수점 형식의 기본값은 `0`입니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="1ca53-123">각 부동 소수점 형식에는 해당 형식의 최소 및 최대 유한값을 제공하는 `MinValue` 및 `MaxValue` 상수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="1ca53-124">또한 `float` 및 `double` 형식은 숫자가 아닌 무한 값을 나타내는 상수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="1ca53-125">예를 들어 `double` 형식은 <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 및 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>와 같은 상수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1ca53-126">`decimal` 형식은 `float` 및 `double`보다 정밀도가 높고 범위가 작으므로 재무 및 통화 계산에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="1ca53-127">식에서 [정수](integral-numeric-types.md) 형식과 부동 소수점 형식을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="1ca53-128">이 경우 정수 형식이 부동 소수점 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="1ca53-129">식의 계산은 다음 규칙에 따라 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="1ca53-130">부동 소수점 형식 중 하나가 `double`인 경우 식은 관계형 비교 및 같음에 대한 비교에서 `double` 또는 [bool](../keywords/bool.md)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="1ca53-131">식에 `double` 형식이 없는 경우 식은 같음에 대한 관계형 비교 또는 비교에서 `float` 또는 [bool](../keywords/bool.md)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="1ca53-132">부동 소수점 식에는 다음과 같은 값 집합이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="1ca53-133">양수 및 음수 0</span><span class="sxs-lookup"><span data-stu-id="1ca53-133">Positive and negative zero</span></span>
- <span data-ttu-id="1ca53-134">양수 및 음수 무한대</span><span class="sxs-lookup"><span data-stu-id="1ca53-134">Positive and negative infinity</span></span>
- <span data-ttu-id="1ca53-135">NaN(Not-a-Number) 값</span><span class="sxs-lookup"><span data-stu-id="1ca53-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="1ca53-136">한정된 0이 아닌 값의 집합</span><span class="sxs-lookup"><span data-stu-id="1ca53-136">The finite set of nonzero values</span></span>

<span data-ttu-id="1ca53-137">이러한 값에 대한 자세한 내용은 [IEEE](https://www.ieee.org) 웹 사이트에서 제공되는 이진 부동 소수점 연산에 대한 IEEE 표준을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ca53-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="1ca53-138">[표준 숫자 서식 문자열](../../../standard/base-types/standard-numeric-format-strings.md) 또는 [사용자 지정 숫자 서식 문자열](../../../standard/base-types/custom-numeric-format-strings.md)을 사용하여 부동 소수점 값의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="1ca53-139">부동 소수점 리터럴</span><span class="sxs-lookup"><span data-stu-id="1ca53-139">Floating-point literals</span></span>

<span data-ttu-id="1ca53-140">기본적으로 대입 연산자 오른쪽의 부동 소수점 숫자 리터럴은 `double`로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="1ca53-141">접미사를 사용하여 부동 소수점 또는 정수 리터럴을 특정 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="1ca53-142">`d` 또는 `D` 접미사는 리터럴을 `double`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="1ca53-143">`f` 또는 `F` 접미사는 리터럴을 `float`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="1ca53-144">`m` 또는 `M` 접미사는 리터럴을 `decimal`로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="1ca53-145">다음 예제는 각 접미사를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="1ca53-146">변환</span><span class="sxs-lookup"><span data-stu-id="1ca53-146">Conversions</span></span>

<span data-ttu-id="1ca53-147">`float` 값의 범위는 `double`의 적절한 하위 집합이고 `float`에서 `double`까지의 정밀도 손실이 없으므로 `float`에서 `double`로의 암시적 변환(*확대 변환*이라고 함)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="1ca53-148">암시적 변환이 소스 유형에서 대상 유형으로 정의되지 않은 경우 명시적 캐스트를 사용하여 하나의 부동 소수점 형식을 다른 부동 소수점 형식으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="1ca53-149">이를 *축소 변환*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="1ca53-150">변환이 데이터 손실을 초래할 수 있기 때문에 명시적인 사례가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="1ca53-151">`decimal` 유형은 `float` 또는 `double`보다 더 높은 정밀도를 가지므로 다른 부동 소수점 형식과 `decimal` 형식 간의 암시적 변환은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca53-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="1ca53-152">암시적 숫자 변환에 대한 자세한 내용은 [암시적 숫자 변환 표](../keywords/implicit-numeric-conversions-table.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ca53-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="1ca53-153">명시적 숫자 변환에 대한 자세한 내용은 [명시적 숫자 변환 표](../keywords/explicit-numeric-conversions-table.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ca53-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca53-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ca53-154">See also</span></span>

- [<span data-ttu-id="1ca53-155">C# 참조</span><span class="sxs-lookup"><span data-stu-id="1ca53-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ca53-156">정수 형식</span><span class="sxs-lookup"><span data-stu-id="1ca53-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="1ca53-157">기본 제공 형식 표</span><span class="sxs-lookup"><span data-stu-id="1ca53-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="1ca53-158">.NET의 숫자</span><span class="sxs-lookup"><span data-stu-id="1ca53-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="1ca53-159">캐스팅 및 형식 변환</span><span class="sxs-lookup"><span data-stu-id="1ca53-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="1ca53-160">암시적 숫자 변환 표</span><span class="sxs-lookup"><span data-stu-id="1ca53-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="1ca53-161">명시적 숫자 변환 표</span><span class="sxs-lookup"><span data-stu-id="1ca53-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="1ca53-162">숫자 결과 형식 지정 표</span><span class="sxs-lookup"><span data-stu-id="1ca53-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="1ca53-163">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="1ca53-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
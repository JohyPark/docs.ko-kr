---
title: System.object의 DateTime 및 DateTimeOffset 지원
description: DateTime 및 DateTimeOffset 형식이 System.object 라이브러리에서 지원 되는 방법에 대 한 개요입니다.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973217"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="66a20-103">System.object의 DateTime 및 DateTimeOffset 지원</span><span class="sxs-lookup"><span data-stu-id="66a20-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="66a20-104">System.string 라이브러리는 ISO 8601:-2019 확장 프로필에 따라 및 <xref:System.DateTime> <xref:System.DateTimeOffset> 값을 구문 분석 하 고 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="66a20-105">[변환기](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) 는로 serialize 및 deserialize 할 수 있는 <xref:System.Text.Json.JsonSerializer>사용자 지정 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="66a20-106">ISO 8601-1:2019 형식에 대 한 지원</span><span class="sxs-lookup"><span data-stu-id="66a20-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="66a20-107"><xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader> ,,및<xref:System.Text.Json.JsonElement> 형식은 ISO 8601-1:2019 형식의 확장 프로필 ( <xref:System.DateTimeOffset> 예: 2019-07-26t16)에 따라 구문 분석 되 고텍스트표현을작성합니다.<xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.JsonSerializer> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="66a20-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="66a20-108"><xref:System.DateTime>다음 <xref:System.DateTimeOffset> 을 사용 하 여 <xref:System.Text.Json.JsonSerializer>및 데이터를 직렬화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="66a20-109">다음을 사용 하 여 <xref:System.Text.Json.JsonSerializer>deserialize 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="66a20-110">기본 옵션을 사용 하 <xref:System.DateTime> 여 <xref:System.DateTimeOffset> 입력 및 텍스트 표현은 확장 된 ISO 8601-1:2019 프로필을 준수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="66a20-111">프로필에 맞지 않는 표현을 deserialize 하려고 하면이 <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="66a20-112">는 <xref:System.Text.Json.JsonDocument> <xref:System.DateTime> 및 표현을<xref:System.DateTimeOffset> 포함 하 여 JSON 페이로드의 내용에 대 한 구조적 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="66a20-113">아래 예제에서는 온도 수집이 지정 된 경우 월요일의 평균 온도를 계산할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="66a20-114">비준수 <xref:System.DateTime> 표현이 포함 된 페이로드에 대해 평균 온도를 계산 하려고 시도 하면 <xref:System.Text.Json.JsonDocument> 이 throw <xref:System.FormatException>됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="66a20-115">낮은 수준 <xref:System.Text.Json.Utf8JsonWriter> 에서 및 <xref:System.DateTime> <xref:System.DateTimeOffset> 데이터를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="66a20-116"><xref:System.Text.Json.Utf8JsonReader>구문 <xref:System.DateTime> 분석 <xref:System.DateTimeOffset> 및 데이터:</span><span class="sxs-lookup"><span data-stu-id="66a20-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="66a20-117">호환 되지 않는 형식을로 <xref:System.Text.Json.Utf8JsonReader> 읽으려고 하면이 <xref:System.FormatException>throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="66a20-118">의 및 <xref:System.DateTime> <xref:System.DateTimeOffset> 에 대 한 사용자 지정 지원<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="66a20-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="66a20-119">Serializer에서 사용자 지정 구문 분석 또는 서식 지정을 수행 하려는 경우 [사용자 지정 변환기](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="66a20-120">다음은 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="66a20-121">및 `DateTime(Offset).Parse` 사용`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="66a20-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="66a20-122">입력 <xref:System.DateTime> `DateTime(Offset).Parse` 또는 <xref:System.DateTimeOffset> 텍스트 표현의 형식을 확인할 수 없는 경우 변환기의 읽기 논리에서 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="66a20-123">이렇게 하면를 사용할 수 있습니다. Iso 8601 문자열 및 확장 된 iso <xref:System.DateTime> 8601-1:2019 <xref:System.DateTimeOffset> 프로필을 준수 하지 않는 iso 8601 형식을 비롯 한 다양 한 텍스트 형식 구문 분석을 위한 광범위 한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="66a20-124">이 방법은 serializer의 기본 구현을 사용 하는 것 보다 성능이 훨씬 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="66a20-125">Serialize를 위해 변환기 쓰기 논리에서 `DateTime(Offset).ToString` 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="66a20-126"><xref:System.DateTime> 이를 통해 [표준 날짜 및 시간 형식](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)및 [사용자 지정 날짜 및 시간 형식을](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)사용 하 여 및 <xref:System.DateTimeOffset> 값을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="66a20-127">이는 serializer의 기본 구현을 사용 하는 것 보다 성능이 훨씬 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="66a20-128">을 구현 <xref:System.Text.Json.Serialization.JsonConverter%601>하 고 `T` 가 <xref:System.DateTime>인 경우 `typeToConvert` 매개 변수는 항상 `typeof(DateTime)`입니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="66a20-129">매개 변수는 다형성 사례를 처리 하 고 제네릭을 사용 하 여 성능을 `typeof(T)` 향상 시킬 때 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="66a20-130">및 <xref:System.Buffers.Text.Utf8Parser> 사용<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="66a20-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="66a20-131">입력 <xref:System.DateTime> 또는<xref:System.DateTimeOffset> 텍스트 표현이 "R", "l", "O" 또는 "G" [표준 날짜 및 시간 형식 문자열](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)중 하나를 준수 하는 경우 변환기 논리에서 빠른 utf-8 기반 구문 분석 및 형식 지정 메서드를 사용할 수 있습니다. 다음 형식 중 하나에 따라 씁니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="66a20-132">이는 및 `DateTime(Offset).ToString`을 사용 하 `DateTime(Offset).Parse` 는 것 보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="66a20-133">이 예제에서는 ["R" 표준 형식](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)에 따라 <xref:System.DateTime> 값을 serialize 및 deserialize 하는 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="66a20-134">"R" 표준 형식은 항상 29 자 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="66a20-135">Serializer `DateTime(Offset).Parse` 의 네이티브 구문 분석에 대 한 대체로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="66a20-136">일반적으로 입력 <xref:System.DateTime> 또는 <xref:System.DateTimeOffset> 데이터가 확장 된 ISO 8601-1:2019 프로필을 따르도록 하려면 serializer의 네이티브 구문 분석 논리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="66a20-137">경우에만 대체 메커니즘을 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="66a20-138">이 예제에서는를 사용 하 여 <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>텍스트 표현의 구문 분석에 실패 한 후 변환기에서를 사용 하 여 <xref:System.DateTime.Parse(System.String)>데이터를 성공적으로 구문 분석 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="66a20-139">System.object의 확장 된 ISO 8601-1:2019 프로필</span><span class="sxs-lookup"><span data-stu-id="66a20-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="66a20-140">날짜 및 시간 구성 요소</span><span class="sxs-lookup"><span data-stu-id="66a20-140">Date and time components</span></span>

<span data-ttu-id="66a20-141">에 <xref:System.Text.Json> 구현 된 확장 ISO 8601-1:2019 프로필은 날짜 및 시간 표현에 대해 다음과 같은 구성 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="66a20-142">이러한 구성 요소는 구문 분석 및 형식 지정 <xref:System.DateTime> 및 <xref:System.DateTimeOffset> 표현을 할 때 지원 되는 다양 한 수준의 세분성을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="66a20-143">구성 요소</span><span class="sxs-lookup"><span data-stu-id="66a20-143">Component</span></span>       | <span data-ttu-id="66a20-144">형식</span><span class="sxs-lookup"><span data-stu-id="66a20-144">Format</span></span>                      | <span data-ttu-id="66a20-145">Description</span><span class="sxs-lookup"><span data-stu-id="66a20-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="66a20-146">Year</span><span class="sxs-lookup"><span data-stu-id="66a20-146">Year</span></span>            | <span data-ttu-id="66a20-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="66a20-147">"yyyy"</span></span>                      | <span data-ttu-id="66a20-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="66a20-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="66a20-149">Month</span><span class="sxs-lookup"><span data-stu-id="66a20-149">Month</span></span>           | <span data-ttu-id="66a20-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="66a20-150">"MM"</span></span>                        | <span data-ttu-id="66a20-151">01-12</span><span class="sxs-lookup"><span data-stu-id="66a20-151">01-12</span></span>                                                                           |
| <span data-ttu-id="66a20-152">Day</span><span class="sxs-lookup"><span data-stu-id="66a20-152">Day</span></span>             | <span data-ttu-id="66a20-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="66a20-153">"dd"</span></span>                        | <span data-ttu-id="66a20-154">월/연도를 기준으로 하는 01-28, 01-29, 01-30, 01-31</span><span class="sxs-lookup"><span data-stu-id="66a20-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="66a20-155">Hour</span><span class="sxs-lookup"><span data-stu-id="66a20-155">Hour</span></span>            | <span data-ttu-id="66a20-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="66a20-156">"HH"</span></span>                        | <span data-ttu-id="66a20-157">00-23</span><span class="sxs-lookup"><span data-stu-id="66a20-157">00-23</span></span>                                                                           |
| <span data-ttu-id="66a20-158">Minute</span><span class="sxs-lookup"><span data-stu-id="66a20-158">Minute</span></span>          | <span data-ttu-id="66a20-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="66a20-159">"mm"</span></span>                        | <span data-ttu-id="66a20-160">00-59</span><span class="sxs-lookup"><span data-stu-id="66a20-160">00-59</span></span>                                                                           |
| <span data-ttu-id="66a20-161">Second</span><span class="sxs-lookup"><span data-stu-id="66a20-161">Second</span></span>          | <span data-ttu-id="66a20-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="66a20-162">"ss"</span></span>                        | <span data-ttu-id="66a20-163">00-59</span><span class="sxs-lookup"><span data-stu-id="66a20-163">00-59</span></span>                                                                           |
| <span data-ttu-id="66a20-164">초 분수</span><span class="sxs-lookup"><span data-stu-id="66a20-164">Second fraction</span></span> | <span data-ttu-id="66a20-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="66a20-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="66a20-166">최소 1 자리 숫자, 최대 16 자리</span><span class="sxs-lookup"><span data-stu-id="66a20-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="66a20-167">시간 오프셋</span><span class="sxs-lookup"><span data-stu-id="66a20-167">Time offset</span></span>     | <span data-ttu-id="66a20-168">"K"</span><span class="sxs-lookup"><span data-stu-id="66a20-168">"K"</span></span>                         | <span data-ttu-id="66a20-169">"Z" 또는 "(' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="66a20-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="66a20-170">부분 시간</span><span class="sxs-lookup"><span data-stu-id="66a20-170">Partial time</span></span>    | <span data-ttu-id="66a20-171">"HH ': ' mm ': ' ss [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="66a20-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="66a20-172">UTC 오프셋 정보가 없는 시간</span><span class="sxs-lookup"><span data-stu-id="66a20-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="66a20-173">전체 날짜</span><span class="sxs-lookup"><span data-stu-id="66a20-173">Full date</span></span>       | <span data-ttu-id="66a20-174">"yyyy'-'mm'-'dd't'hh-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="66a20-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="66a20-175">달력 날짜</span><span class="sxs-lookup"><span data-stu-id="66a20-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="66a20-176">전체 시간</span><span class="sxs-lookup"><span data-stu-id="66a20-176">Full time</span></span>       | <span data-ttu-id="66a20-177">"' Partial time'K"</span><span class="sxs-lookup"><span data-stu-id="66a20-177">"'Partial time'K"</span></span>           | <span data-ttu-id="66a20-178">현지 시간과 UTC 사이의 시간 오프셋을 사용한 하루 또는 현지 시간 (UTC)</span><span class="sxs-lookup"><span data-stu-id="66a20-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="66a20-179">날짜 시간</span><span class="sxs-lookup"><span data-stu-id="66a20-179">Date time</span></span>       | <span data-ttu-id="66a20-180">"' 전체 날짜 ' ' ' ' 전체 시간 '"</span><span class="sxs-lookup"><span data-stu-id="66a20-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="66a20-181">달력 날짜 및 시간 (예: 2019-07-26T16:59:57-05:00)</span><span class="sxs-lookup"><span data-stu-id="66a20-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="66a20-182">구문 분석 지원</span><span class="sxs-lookup"><span data-stu-id="66a20-182">Support for parsing</span></span>

<span data-ttu-id="66a20-183">구문 분석에 대해 정의 되는 세분성 수준은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="66a20-184">' 전체 날짜 '</span><span class="sxs-lookup"><span data-stu-id="66a20-184">'Full date'</span></span>
    1. <span data-ttu-id="66a20-185">"yyyy'-'mm'-'dd't'hh-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="66a20-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="66a20-186">"' 전체 날짜 ' ' ' ' ' 시간 ' ': ' ' Minute '"</span><span class="sxs-lookup"><span data-stu-id="66a20-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="66a20-187">"yyyy'-'mm'-'dd't'hh-'MM'-' m ': ' MM '</span><span class="sxs-lookup"><span data-stu-id="66a20-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="66a20-188">"' 전체 날짜 ' ' ' ' ' 부분 시간 '"</span><span class="sxs-lookup"><span data-stu-id="66a20-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="66a20-189">"yyyy'-'mm'-'dd't'hh-'MM'-% Ddu: ' MM ': ' ss ' ([정렬 가능한 (" s ") 서식 지정자](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="66a20-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="66a20-190">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="66a20-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="66a20-191">"' 전체 날짜 ' ' ' ' 시간 시간 ' ': ' ' Minute ' ' 시간 오프셋 '"</span><span class="sxs-lookup"><span data-stu-id="66a20-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="66a20-192">"yyyy'-'mm'-'dd't'hh-'MM'-% n n e t ': ' mmZ '</span><span class="sxs-lookup"><span data-stu-id="66a20-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="66a20-193">"yyyy'-'mm'-'dd't'hh-'MM'-% Ddn ': ' mm (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="66a20-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="66a20-194">' 날짜 시간 '</span><span class="sxs-lookup"><span data-stu-id="66a20-194">'Date time'</span></span>
    1. <span data-ttu-id="66a20-195">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="66a20-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="66a20-196">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="66a20-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="66a20-197">"yyyy'-'mm'-'dd't'hh-'MM'-% n n e t ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="66a20-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="66a20-198">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="66a20-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="66a20-199">초에 소수 자릿수가 있으면 숫자가 하나 이상 있어야 합니다. `2019-07-26T00:00:00.` 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="66a20-200">최대 16 개의 소수 자릿수가 허용 되지만 처음 7 개만 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="66a20-201">그 외의 모든 항목은 0으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="66a20-202">예 `2019-07-26T00:00:00.1234567890` 를 들어는 `2019-07-26T00:00:00.1234567`인 것 처럼 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="66a20-203">이는이 해상도로 제한 되 <xref:System.DateTime> 는 구현과의 호환성을 유지 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="66a20-204">윤 초는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="66a20-205">서식 지정 지원</span><span class="sxs-lookup"><span data-stu-id="66a20-205">Support for formatting</span></span>

<span data-ttu-id="66a20-206">서식 지정에 대해 정의 된 세분성 수준은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="66a20-207">"' 전체 날짜 ' ' ' ' ' 부분 시간 '"</span><span class="sxs-lookup"><span data-stu-id="66a20-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="66a20-208">"yyyy'-'mm'-'dd't'hh-'MM'-% Ddu: ' MM ': ' ss ' ([정렬 가능한 (" s ") 서식 지정자](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="66a20-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="66a20-209">오프셋 정보 없이 소수 <xref:System.DateTime> 자릿수 초 없이의 형식을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="66a20-210">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="66a20-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="66a20-211">오프셋 정보 없이 소수 <xref:System.DateTime> 자릿수 초를 사용 하 여의 형식을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="66a20-212">' 날짜 시간 '</span><span class="sxs-lookup"><span data-stu-id="66a20-212">'Date time'</span></span>
    1. <span data-ttu-id="66a20-213">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="66a20-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="66a20-214">소수 자릿수 초를 <xref:System.DateTime> 제외 <xref:System.DateTimeOffset> 하 고 UTC 오프셋을 사용 하 여의 형식을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="66a20-215">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="66a20-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="66a20-216">UTC 오프셋을 사용 <xref:System.DateTime> 하 <xref:System.DateTimeOffset> 여 또는 소수 자릿수 초를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="66a20-217">"yyyy'-'mm'-'dd't'hh-'MM'-% n n e t ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="66a20-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="66a20-218">소수 자릿수 초를 <xref:System.DateTime> 제외 <xref:System.DateTimeOffset> 하 고 로컬 오프셋을 사용 하 여의 형식을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="66a20-219">"yyyy'-'mm'-'dd't'hh-'MM'-% n이 (가): ' MM ': ' ss '. ' FFFFFFF (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="66a20-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="66a20-220">현지 오프셋으로 또는 <xref:System.DateTime> <xref:System.DateTimeOffset> 소수 자릿수 초를 사용 하 여의 형식을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66a20-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
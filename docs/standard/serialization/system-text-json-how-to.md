---
title: C#을 사용하여 JSON을 직렬화 및 역직렬화하는 방법 - .NET
description: 이 문서에서는 System.Text.Json 네임스페이스를 사용하여 .NET에서 JSON으로 직렬화 및 역직렬화하는 방법을 보여 줍니다. 샘플 코드가 포함되어 있습니다.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 7ad2721f12c5d14b61b35ecf7696ff0d6a6f27da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289514"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET에서 JSON을 직렬화 및 역직렬화(마샬링 및 역 마샬링)하는 방법

이 문서에서는 <xref:System.Text.Json> 네임스페이스를 사용하여 JSON(JavaScript Object Notation)으로/에서 직렬화 및 역직렬화하는 방법을 보여줍니다. `Newtonsoft.Json`에서 기존 코드를 이식하는 경우 [`System.Text.Json`으로 마이그레이션 방법](system-text-json-migrate-from-newtonsoft-how-to.md)을 참조하세요.

지침 및 샘플 코드에서는 [ASP.NET Core](/aspnet/core/) 같은 프레임워크를 통하지 않고 직접 라이브러리를 사용합니다.

대부분의 직렬화 샘플 코드는 JSON을 "보기 좋게 출력"하도록(사람이 읽기 쉽도록 들여쓰기 및 공백 사용) <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType>을 `true`로 설정합니다. 프로덕션에 사용하는 경우에는 일반적으로 이 설정의 기본값인 `false`를 적용합니다.

코드 예제에서는 다음 클래스와 그 변형을 참조합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>네임스페이스

<xref:System.Text.Json> 네임스페이스에는 모든 진입점과 기본 형식이 포함되어 있습니다. <xref:System.Text.Json.Serialization> 네임스페이스에는 직렬화 및 역직렬화와 관련된 고급 시나리오 및 사용자 지정을 위한 특성과 API가 포함되어 있습니다. 이 문서의 코드 예제에서는 두 네임스페이스 중 하나 또는 둘 다에 `using` 지시문이 필요합니다.

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> 네임스페이스의 특성은 현재 `System.Text.Json`에서 지원되지 않습니다.

## <a name="how-to-write-net-objects-to-json-serialize"></a>JSON에 .NET 개체를 쓰는 방법(직렬화)

문자열 또는 파일에 JSON을 쓰려면 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 메서드를 호출합니다.

다음은 JSON 파일을 문자열로 만드는 예제입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

다음은 동기 코드를 사용하여 JSON 파일을 만드는 예제입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

다음은 비동기 코드를 사용하여 JSON 파일을 만드는 예제입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

앞의 예제에서는 직렬화되는 형식에 형식 유추를 사용합니다. `Serialize()`의 오버로드는 제네릭 형식 매개 변수를 사용합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>직렬화 예제

다음은 컬렉션 및 중첩 클래스를 포함하는 클래스 예제입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

다음은 이전 형식의 인스턴스를 직렬화하는 JSON 출력의 예입니다. JSON 출력은 기본적으로 축소됩니다.

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

다음 예제에서는 동일한 JSON 형식(공백 및 들여쓰기를 사용하여 보기 좋게 인쇄됨)을 보여줍니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a>UTF-8로 직렬화

UTF-8로 직렬화하려면 다음과 같이 <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 메서드를 호출합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<xref:System.Text.Json.Utf8JsonWriter>를 사용하는 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 오버로드도 사용할 수 있습니다.

UTF-8로 직렬화하면 문자열 기반 메서드를 사용할 때보다 약 5-10% 더 빠릅니다. 속도에서 차이가 나는 이유는 바이트(UTF-8)를 문자열(UTF-16)로 변환할 필요가 없기 때문입니다.

## <a name="serialization-behavior"></a>Serialization 동작

* 기본적으로 모든 public 속성은 직렬화됩니다. [제외할 속성을 지정](#exclude-properties-from-serialization)할 수 있습니다.
* [기본 인코더](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)는 ASCII가 아닌 문자, ASCII 범위 내의 HTML 구분 문자 및 [RFC 8259 JSON 사양](https://tools.ietf.org/html/rfc8259#section-7)에 따라 이스케이프되어야 하는 문자를 이스케이프합니다.
* 기본적으로 JSON은 축소됩니다. [JSON을 보기 좋게 출력](#serialize-to-formatted-json)할 수 있습니다.
* 기본적으로 JSON 이름의 대/소문자는 .NET 이름과 일치합니다. [JSON 이름 대/소문자를 사용자 지정](#customize-json-names-and-values)할 수 있습니다.
* 순환 참조가 감지되고 예외가 throw됩니다.
* 현재는 필드가 제외됩니다.

지원되는 형식은 다음과 같습니다.

* 숫자 형식, 문자열, 부울 등 JavaScript 기본 형식에 매핑되는 .NET 기본 형식
* 사용자 정의 [POCO(Plain Old CLR Object)](https://stackoverflow.com/questions/250001/poco-definition)
* 1차원 및 가변 배열(`ArrayName[][]`)
* `Dictionary<string,TValue>`. 여기서 `TValue`는 `object`, `JsonElement` 또는 POCO입니다.
* 다음 네임스페이스의 컬렉션.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

추가 형식을 처리하거나 기본 변환기에서 지원하지 않는 기능을 제공하는 [사용자 지정 변환기를 구현](system-text-json-converters-how-to.md)할 수 있습니다.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON을 .NET 개체로 읽는 방법(역직렬화)

문자열 또는 파일에서 역직렬화하려면 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 메서드를 호출합니다.

다음 예제에서는 문자열에서 JSON을 읽고, 앞에서 [직렬화 예제](#serialization-example)에서 설명한 `WeatherForecast` 클래스의 인스턴스를 만듭니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

동기 코드를 사용하여 파일에서 역직렬화하려면 다음 예제와 같이 파일을 문자열로 읽습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

비동기 코드를 사용하여 파일에서 역직렬화하려면 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> 메서드를 호출합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>UTF-8에서 역직렬화

UTF-8에서 역직렬화하려면 다음 예제와 같이 `Utf8JsonReader` 또는 `ReadOnlySpan<byte>`을 사용하는 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 오버로드를 호출합니다. 이 예제에서는 JSON이 jsonUtf8Bytes라는 바이트 배열에 있다고 가정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>역직렬화 동작

* 속성 이름 일치 시에 대/소문자를 구분합니다. [대/소문자를 구분 하지 않도록 지정](#case-insensitive-property-matching)할 수 있습니다.
* JSON에 읽기 전용 속성의 값이 포함되어 있으면 해당 값이 무시되고 예외가 throw되지 않습니다.
* 매개 변수 없는 생성자가 없는 참조 형식으로의 역직렬화는 지원되지 않습니다.
* 변경할 수 없는 개체 또는 읽기 전용 속성으로의 역직렬화는 지원되지 않습니다.
* 기본적으로 열거형은 숫자로 지원됩니다. [열거형 이름을 문자열로 직렬화](#enums-as-strings)할 수 있습니다.
* 필드는 지원되지 않습니다.
* 기본적으로 JSON의 주석이나 후행 쉼표는 예외를 throw합니다. [주석과 후행 쉼표를 허용](#allow-comments-and-trailing-commas)할 수 있습니다.
* [기본 최댓값](xref:System.Text.Json.JsonReaderOptions.MaxDepth)은 64입니다.

기본 변환기에서 지원하지 않는 기능을 제공하는 [사용자 지정 변환기를 구현](system-text-json-converters-how-to.md)할 수 있습니다.

## <a name="serialize-to-formatted-json"></a>형식이 지정된 JSON으로 직렬화

JSON 출력을 보기 좋게 출력하려면 <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType>을 `true`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

다음 형식은 직렬화하여 보기 좋게 출력할 JSON 출력의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>JSON 이름 및 값 사용자 지정

기본적으로 대/소문자를 비롯한 속성 이름 및 사전 키는 JSON 출력에서 변경되지 않습니다. 열거형 값은 숫자로 표시됩니다. 이 섹션에서는 다음을 수행하는 방법을 설명합니다.

* [개별 속성 이름 사용자 지정](#customize-individual-property-names)
* [모든 속성 이름을 카멜식 대/소문자로 변환](#use-camel-case-for-all-json-property-names)
* [사용자 지정 속성 명명 정책 구현](#use-a-custom-json-property-naming-policy)
* [사전 키를 카멜식 대/소문자로 변환](#camel-case-dictionary-keys)
* [열거형을 문자열 및 카멜식 대/소문자로 변환](#enums-as-strings)

JSON 속성 이름 및 값을 특수하게 처리해야 하는 다른 시나리오의 경우 [사용자 지정 변환기를 구현](system-text-json-converters-how-to.md)하면 됩니다.

### <a name="customize-individual-property-names"></a>개별 속성 이름 사용자 지정

개별 속성 이름을 설정하려면 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 특성을 사용합니다.

다음은 직렬화 형식과 그 결과 JSON의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

이 특성을 통해 설정된 속성 이름은 다음과 같은 특징이 있습니다.

* 직렬화 및 역직렬화 양방향으로 적용됩니다.
* 속성 명명 정책보다 우선합니다.

### <a name="use-camel-case-for-all-json-property-names"></a>모든 JSON 속성 이름에 카멜식 대/소문자 사용

모든 JSON 속성 이름에 카멜식 대/소문자를 사용하려면 다음 예제와 같이 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType>을 `JsonNamingPolicy.CamelCase`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

다음은 직렬화 클래스 및 JSON 출력의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

카멜식 대/소문자 속성 명명 정책은 다음과 같습니다.

* 직렬화 및 역직렬화에 적용됩니다.
* `[JsonPropertyName]` 특성에 의해 재정의됩니다. 이러한 이유로 이 예제의 JSON 속성 이름 `Wind`는 카멜식 대/소문자가 아닙니다.

### <a name="use-a-custom-json-property-naming-policy"></a>사용자 지정 JSON 속성 명명 정책 사용

사용자 지정 JSON 속성 명명 정책을 사용하려면 다음 예제와 같이 <xref:System.Text.Json.JsonNamingPolicy>에서 파생되는 클래스를 만들고 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 메서드를 재정의합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

그리고 다음과 같이 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 속성을 명명 정책 클래스의 인스턴스로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

다음은 직렬화 클래스 및 JSON 출력의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

JSON 속성 명명 정책은 다음과 같습니다.

* 직렬화 및 역직렬화에 적용됩니다.
* `[JsonPropertyName]` 특성에 의해 재정의됩니다. 이러한 이유로 이 예제의 JSON 속성 이름 `Wind`는 대문자가 아닙니다.

### <a name="camel-case-dictionary-keys"></a>카멜식 대/소문자 사전 키

직렬화할 개체의 속성이 `Dictionary<string,TValue>` 형식이면 `string` 키를 카멜식 대/소문자로 변환할 수 있습니다. 이렇게 하려면 다음 예제와 같이 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy>를 `JsonNamingPolicy.CamelCase`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

키-값 쌍 `"ColdMinTemp", 20` 및 `"HotMinTemp", 40`가 있는 `TemperatureRanges`라는 사전이 포함된 개체를 직렬화하면 다음 예제와 같은 JSON 출력이 생성됩니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

사전 키에 대한 카멜식 대/소문자 명명 정책은 직렬화에만 적용됩니다. 사전을 역직렬화하면 `DictionaryKeyPolicy`에 대 한 `JsonNamingPolicy.CamelCase`를 지정하더라도 키가 JSON 파일과 일치합니다.

### <a name="enums-as-strings"></a>문자열인 열거형

기본적으로 열거형은 숫자로 직렬화됩니다. 열거형 이름을 문자열로 직렬화하려면 <xref:System.Text.Json.Serialization.JsonStringEnumConverter>를 사용합니다.

예를 들어 열거형을 포함하는 다음 클래스를 직렬화해야 한다고 가정해 봅시다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Summary가 `Hot`이면 기본적으로 직렬화된 JSON은 다음과 같이 숫자 값 3을 갖습니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

다음 샘플 코드는 숫자 값 대신 열거형 이름을 직렬화하고, 이름을 카멜식 대/소문자로 변환합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

그 결과로 얻는 JSON은 다음 예제와 유사합니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

다음 예제와 같이 열거형 문자열 이름도 역직렬화할 수 있습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>직렬화에서 속성 제외

기본적으로 모든 public 속성은 직렬화됩니다. 그 중 일부 속성을 JSON 출력에 표시하지 않으려는 경우에 사용할 수 있는 몇 가지 옵션이 있습니다. 이 섹션에서는 다음 속성을 제외하는 방법을 설명합니다.

* [개별 속성](#exclude-individual-properties)
* [모든 읽기 전용 속성](#exclude-all-read-only-properties)
* [모든 Null 값 속성](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>개별 속성 제외

개별 속성을 무시하려면 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 특성을 사용합니다.

다음은 직렬화 형식 및 JSON 출력의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>모든 읽기 전용 속성 제외

public setter가 아닌 public getter를 포함하는 속성은 읽기 전용입니다. 모든 읽기 전용 속성을 제외하려면 다음 예제와 같이 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType>을 `true`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

다음은 직렬화 형식 및 JSON 출력의 예입니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

이 옵션은 직렬화에만 적용됩니다. 역직렬화를 수행할 때 읽기 전용 속성은 기본적으로 무시됩니다.

### <a name="exclude-all-null-value-properties"></a>모든 Null 값 속성 제외

모든 Null 값 속성을 제외하려면 다음 예제와 같이 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 속성을 `true`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

다음은 직렬화 개체 및 JSON 출력의 예입니다.

|속성 |값  |
|---------|---------|
| 날짜    | 8/1/2019 12:00:00 AM -07:00|
| TemperatureCelsius| 25 |
| 요약| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

이 설정은 직렬화 및 역직렬화에 적용됩니다. 역직렬화에 미치는 영향에 대한 자세한 내용은 [역직렬화할 때 Null 무시](#ignore-null-when-deserializing)를 참조하세요.

## <a name="customize-character-encoding"></a>문자 인코딩 사용자 지정

기본적으로 직렬 변환기는 ASCII가 아닌 문자를 모두 이스케이프합니다.  즉, ASCII가 아닌 문자를 `\uxxxx`로 바꾸며, 여기서 `xxxx`는 문자의 유니코드 코드입니다.  예를 들어 `Summary` 속성이 키릴 자모로 설정된 경우 다음 예제와 같이 `WeatherForecast` 개체가 직렬화됩니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>언어 문자 세트 직렬화

하나 이상의 언어 문자 세트를 이스케이프하지 않고 직렬화하려면 다음 예제와 같이 <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> 인스턴스를 만들 때 [유니코드 범위](xref:System.Text.Unicode.UnicodeRanges)를 지정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

이 코드는 키릴 자모 또는 그리스어 문자를 이스케이프하지 않습니다. `Summary` 속성이 키릴 자모로 설정된 경우 `WeatherForecast` 개체는 다음 예제와 같이 직렬화됩니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

모든 언어 세트를 이스케이프하지 않고 직렬화하려면 <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>을 사용합니다.

### <a name="serialize-specific-characters"></a>특정 문자 직렬화

이스케이프하지 않고 허용하려는 개별 문자를 지정하는 방법도 있습니다. 다음 예제에서는 키릴 자모의 처음 두 문자만 직렬화합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

다음은 이전 코드에서 생성된 JSON 예제입니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>모든 문자 직렬화

이스케이프를 최소화하려면 다음 예제와 같이 <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>을 사용합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> 기본 인코더와 비교할 때, `UnsafeRelaxedJsonEscaping` 인코더는 문자를 이스케이프하지 않은 상태로 통과할 수 있도록 허용하는 기준이 더 관대합니다.
>
> * `<`, `>`, `&` 및 `'`처럼 HTML 구분 문자를 이스케이프하지 않습니다.
> * *문자 세트*에 대한 클라이언트와 서버의 내용이 서로 다를 때 발생할 수 있는 XSS 또는 정보 노출 공격에 대한 심층 방어를 추가로 제공하지 않습니다.
>
> 클라이언트가 결과 페이로드를 UTF-8로 인코딩된 JSON으로 해석한다는 사실을 알고 있는 경우에만 안전하지 않은 인코더를 사용해야 합니다. 예를 들어 서버에서 응답 헤더 `Content-Type: application/json; charset=utf-8`을 보내는 경우에 사용할 수 있습니다. 원시 `UnsafeRelaxedJsonEscaping` 출력을 HTML 페이지나 `<script>` 요소로 내보내도록 허용하면 절대 안 됩니다.

## <a name="serialize-properties-of-derived-classes"></a>파생 클래스의 속성 직렬화

다형 형식 계층 구조의 직렬화는 지원되지 않습니다. 예를 들어 속성이 인터페이스 또는 추상 클래스로 정의된 경우에는 런타임 형식에 추가 속성이 있더라도 인터페이스 또는 추상 클래스에 정의된 속성만 직렬화됩니다. 이 동작의 예외는 이 섹션에 설명되어 있습니다.

예를 들어 `WeatherForecast` 클래스와 `WeatherForecastDerived` 파생 클래스가 있다고 가정해 봅시다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

그리고 컴파일 시간에 `Serialize` 메서드의 형식 인수가 `WeatherForecast`라고 가정하겠습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

이 시나리오에서는 `weatherForecast` 개체가 실제로 `WeatherForecastDerived` 개체인 경우에도 `WindSpeed` 속성이 직렬화되지 않습니다. 기본 클래스 속성만 직렬화됩니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

이 동작의 목적은 파생된 런타임 생성 형식에서 실수로 데이터가 노출되는 것을 방지하는 것입니다.

이전 예제의 파생 형식 속성을 직렬화하려면 다음 방법 중 하나를 사용합니다.

* 런타임에 형식을 지정할 수 있는 <xref:System.Text.Json.JsonSerializer.Serialize%2A> 오버로드를 호출합니다.

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* `object`로 직렬화할 개체를 선언합니다.

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

위의 예제 시나리오에서 두 방법 모두 다음과 같이 `WindSpeed` 속성이 JSON 출력에 포함됩니다.

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> 이러한 접근 방식은 루트 개체의 속성이 아니라 직렬화할 루트 개체에 대해서만 다형 직렬화를 제공합니다.

`object` 형식으로 정의하면 하위 수준 개체에 대한 다형 직렬화를 얻을 수 있습니다. 예를 들어 `WeatherForecast` 클래스에 `WeatherForecast` 또는 `object` 형식으로 정의할 수 있는 `PreviousForecast`라는 속성이 있다고 가정하겠습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

이 `PreviousForecast` 속성은 다음과 같이 `WeatherForecastDerived` 인스턴스를 포함합니다.

* `WeatherForecastWithPrevious` 직렬화의 JSON 출력에는 `WindSpeed`가 포함되지 **않습니다**.
* `WeatherForecastWithPreviousAsObject` 직렬화의 JSON 출력에는 `WindSpeed`가 포함**됩니다**.

루트 개체가 파생 형식이 아닐 수도 있으므로 `WeatherForecastWithPreviousAsObject`를 직렬화하기 위해 `Serialize<object>` 또는 `GetType`을 반드시 호출해야 하는 것은 아닙니다. 예를 들어 다음 코드 예제는 `Serialize<object>` 또는 `GetType`을 호출하지 않습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

이전 코드는 다음과 같이 `WeatherForecastWithPreviousAsObject`를 올바르게 직렬화합니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

속성을 `object`로 정의하는 동일한 방법이 인터페이스에서도 작동합니다. 다음과 같은 인터페이스 및 구현이 있고, 구현 인스턴스가 포함된 속성을 사용하여 클래스를 직렬화하려는 경우를 가정해 보겠습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

`Forecasts`의 인스턴스를 직렬화할 경우 `Tuesday`가 `object`로 정의되어 있으므로 `Tuesday`만 `WindSpeed` 속성을 표시합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

다음 예제에서는 이전 코드의 결과로 생성되는 JSON을 보여줍니다.

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

다형 **serialization** 및 **deserialization**에 대한 자세한 내용은 [Newtonsoft.Json에서 System.Text.Json로 마이그레이션하는 방법](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)을 참조하세요.

## <a name="allow-comments-and-trailing-commas"></a>주석과 후행 쉼표 허용

기본적으로 주석과 후행 쉼표는 JSON에서 허용되지 않습니다. JSON에서 주석을 허용하려면 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 속성을 `JsonCommentHandling.Skip`으로 설정합니다.
그리고 후행 쉼표를 허용하려면 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 속성을 `true`로 설정합니다. 다음 예제에서는 주석과 후행 쉼표를 허용하는 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

다음은 주석과 후행 쉼표를 사용하는 JSON 예제입니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>대/소문자를 구분하지 않는 속성 매칭

기본적으로 역직렬화는 JSON과 대상 개체 속성 간에 일치하는 대/소문자 구분 속성 이름을 찾습니다. 이 동작을 변경하려면 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType>을 `true`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

다음은 카멜식 대/소문자 속성 이름을 사용하는 JSON 예제입니다. 파스칼식 대/소문자 속성 이름을 사용하는 다음 형식으로 역직렬화할 수 있습니다.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>오버플로 JSON 처리

역직렬화할 때 대상 형식의 속성으로 표시되지 않는 데이터를 JSON에서 받을 수 있습니다. 예를 들어 대상 형식이 다음과 같다고 가정하겠습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

그리고 역직렬화할 JSON은 다음과 같습니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

표시된 JSON을 표시된 형식으로 역직렬화하면 `DatesAvailable` 및 `SummaryWords` 속성은 이동할 곳이 없으므로 없어집니다. 이러한 속성과 같은 추가 데이터를 캡처하려면 다음과 같이 [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 특성을 `Dictionary<string,object>` 또는 `Dictionary<string,JsonElement>` 형식의 속성에 적용합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

앞에서 보여드린 JSON을 이 샘플 형식으로 역직렬화하면 추가 데이터는 다음과 같이 `ExtensionData` 속성의 키-값 쌍이 됩니다.

|속성 |값  |참고  |
|---------|---------|---------|
| 날짜    | 8/1/2019 12:00:00 AM -07:00||
| TemperatureCelsius| 0 | 대/소문자를 구분하는 불일치(JSON의 `temperatureCelsius`). 따라서 속성이 설정되지 않습니다. |
| 요약 | 핫 ||
| ExtensionData | temperatureCelsius: 25 |대/소문자가 일치하지 않으므로 이 JSON 속성은 추가 속성이며 사전에서 키-값 쌍이 됩니다.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM -07:00<br>8/2/2019 12:00:00 AM -07:00 |JSON의 추가 속성은 키-값 쌍이 되고, 배열은 값 개체로 사용됩니다.|
| |SummaryWords:<br>표<br>Windy<br>Humid |JSON의 추가 속성은 키-값 쌍이 되고, 배열은 값 개체로 사용됩니다.|

대상 개체가 직렬화되면 확장 데이터 키 값 쌍은 마치 수신 JSON에 있는 것처럼 JSON 속성이 됩니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

`ExtensionData` 속성 이름은 JSON에 표시되지 않습니다. 이 동작을 통해 JSON은 추가 데이터를 잃지 않고도 라운드트립을 수행할 수 있으며, 이 동작이 없으면 추가 데이터가 역직렬화되지 않습니다.

## <a name="ignore-null-when-deserializing"></a>역직렬화할 때 Null 무시

기본적으로 JSON의 속성이 Null이면 대상 개체의 해당 속성은 Null로 설정됩니다. 대상 속성에 기본값이 사용되며 기본값이 Null 값으로 재정의되지 않기를 원하는 경우가 있습니다.

예를 들어 다음 코드가 대상 개체를 보여준다고 가정하겠습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

그리고 다음 JSON이 역직렬화된다고 가정하겠습니다.

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

역직렬화 후 `WeatherForecastWithDefault` 개체의 `Summary` 속성은 Null입니다.

이 동작을 변경하려면 다음 예제와 같이 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>을 `true`로 설정합니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

이 옵션을 사용하면 역직렬화 후 `WeatherForecastWithDefault` 개체의 `Summary` 속성은 기본값인 "No summary"입니다.

JSON의 Null 값은 유효한 경우에만 무시됩니다. null을 허용하지 않는 값 형식에 Null 값을 사용하면 예외가 발생합니다.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter 및 JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>은 `ReadOnlySpan<byte>` 또는 `ReadOnlySequence<byte>`에서 읽어온 UTF-8 인코딩 JSON 텍스트를 위한 고성능, 저할당, 전달 전용 판독기입니다. `Utf8JsonReader`는 사용자 지정 구문 분석기 및 역직렬 변환기를 빌드하는 데 활용할 수 있는 하위 수준 형식입니다. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 메서드는 내부적으로 `Utf8JsonReader`를 사용합니다.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>은 `String`, `Int32` 및 `DateTime`과 같은 일반적인 .NET 형식에서 UTF-8 인코딩 JSON 텍스트를 쓸 수 있는 고성능 방법을 제공합니다. writer는 사용자 지정 직렬 변환기를 빌드하는 데 사용할 수 있는 하위 수준 형식입니다. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 메서드는 내부적으로 `Utf8JsonWriter`를 사용합니다.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>은 `Utf8JsonReader`를 사용하여 읽기 전용 DOM(문서 개체 모델)을 빌드하는 기능을 제공합니다. DOM은 JSON 페이로드의 데이터에 대한 임의 액세스를 제공합니다. 페이로드를 구성하는 JSON 요소는 <xref:System.Text.Json.JsonElement> 형식을 통해 액세스할 수 있습니다. `JsonElement` 형식은 JSON 텍스트를 일반적인 .NET 형식으로 변환하는 API와 함께 배열 및 개체 열거자를 제공합니다. `JsonDocument`는 <xref:System.Text.Json.JsonDocument.RootElement> 속성을 노출합니다.

다음 섹션에서는 이러한 도구를 사용하여 JSON을 읽고 쓰는 방법을 보여줍니다.

## <a name="use-jsondocument-for-access-to-data"></a>JsonDocument를 사용하여 데이터 액세스

다음 예제에서는 <xref:System.Text.Json.JsonDocument> 클래스를 사용하여 JSON 문자열의 데이터에 임의로 액세스하는 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

위의 코드는

* 분석할 JSON은 `jsonString`이라는 문자열에 있다고 가정합니다.
* `Grade` 속성이 있는 `Students` 배열의 개체에 대한 평균 등급을 계산합니다.
* 등급이 없는 학생에게 기본 등급 70을 할당합니다.
* 반복마다 `count` 변수를 늘려서 학생 수를 계산합니다. 다음 예제처럼 <xref:System.Text.Json.JsonElement.GetArrayLength%2A>를 호출하는 방법도 있습니다.

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

다음은 이 코드가 처리하는 JSON 예제입니다.

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>JsonDocument를 사용하여 JSON 쓰기

다음 예제에서는 <xref:System.Text.Json.JsonDocument>에서 JSON을 쓰는 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

위의 코드는

* JSON 파일을 읽고, `JsonDocument`에 데이터를 로드하고, 서식 있는(보기 좋게 출력된) JSON을 파일에 씁니다.
* <xref:System.Text.Json.JsonDocumentOptions>를 사용하여 입력 JSON의 주석을 허용하지만 무시하도록 지정합니다.
* 완료되면 writer에서 <xref:System.Text.Json.Utf8JsonWriter.Flush%2A>를 호출합니다. 삭제될 때 writer가 자동으로 플러시하도록 설정하는 방법도 있습니다.

다음은 예제 코드에서 처리할 JSON 입력의 예입니다.

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

결과는 다음과 같이 보기 좋게 출력된 JSON 출력입니다.

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter 사용

다음 예제에서는 <xref:System.Text.Json.Utf8JsonWriter> 클래스 사용 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utf8JsonReader 사용

다음 예제에서는 <xref:System.Text.Json.Utf8JsonReader> 클래스 사용 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

위의 코드는 `jsonUtf8` 변수가 UTF-8로 인코딩된 유효한 JSON을 포함하는 바이트 배열이라고 가정합니다.

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader를 사용하여 데이터 필터링

다음 예제에서는 파일을 동기적으로 읽고 값을 검색하는 방법을 보여줍니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

위의 코드는

* JSON에 개체 배열이 포함되고 각 개체에 문자열 형식의 "name" 속성이 포함될 수 있다고 가정합니다.
* "대학교"로 끝나는 개체 및 "이름" 속성 값의 개수를 계산합니다.
* 파일이 UTF-16으로 인코딩되고 UTF-8로 코드 변환된다고 가정합니다. UTF-8로 인코딩된 파일은 다음 코드를 사용하여 `ReadOnlySpan<byte>`로 직접 읽을 수 있습니다.

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  파일에 UTF-8 BOM(바이트 순서 표시)이 포함된 경우 제거한 후 바이트를 `Utf8JsonReader`에 전달해야 합니다. 판독기에는 텍스트가 필요하기 때문입니다. 그렇지 않으면 BOM은 잘못된 JSON으로 간주되고, 판독기에서 예외를 throw합니다.

다음은 위의 코드에서 읽을 수 있는 JSON 샘플입니다. 다음과 같이 "4개 이름 중 2개가 '대학교'로 끝나는 이름"이라는 결과 요약 메시지가 표시됩니다.

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Utf8JsonReader를 사용하여 스트림에서 읽기

큰 파일(예: 기가바이트 이상 크기)을 읽을 때 전체 파일을 한 번에 메모리에 로드하지 않아도 되는 경우가 있습니다. 이 시나리오에서는 <xref:System.IO.FileStream>을 사용할 수 있습니다.

`Utf8JsonReader`를 사용하여 스트림에서 읽는 경우 다음 규칙이 적용됩니다.

* 부분 JSON 페이로드를 포함하는 버퍼는 판독기가 진행할 수 있도록 최소한 그 안에 있는 가장 큰 JSON 토큰만큼 커야 합니다.
* 버퍼는 최소한 JSON 내에서 가장 큰 공백 시퀀스만큼 커야 합니다.
* 판독기는 JSON 페이로드의 다음 <xref:System.Text.Json.Utf8JsonReader.TokenType%2A>을 완전히 읽을 때까지는 읽은 데이터를 추적하지 않습니다. 따라서 버퍼에 바이트가 남아 있으면 판독기에 다시 전달해야 합니다. <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A>를 사용하여 남은 바이트 수를 확인할 수 있습니다.

다음 코드에서는 스트림에서 읽는 방법을 보여 줍니다. 이 예제에서는 <xref:System.IO.MemoryStream>을 보여 줍니다. `FileStream`이 시작 시 UTF-8 BOM을 포함하는 경우를 제외하고는 <xref:System.IO.FileStream>에서 비슷한 코드가 작동합니다. 이 경우 남은 바이트를 `Utf8JsonReader`에 전달하기 전에 버퍼에서 3바이트를 제거해야 합니다. 그렇지 않으면 BOM이 JSON의 유효한 부분으로 간주되지 않으므로 판독기가 예외를 throw합니다.

이 샘플 코드는 4KB 버퍼로 시작하여 크기가 부족하여 전체 JSON 토큰을 수용할 수 없을 때마다 버퍼 크기를 두 배로 늘립니다. 이는 판독기가 JSON 페이로드에 대한 작업을 진행하는 데 필요합니다. 이 코드 조각에 제공된 JSON 샘플은 10바이트와 같이 매우 작은 초기 버퍼 크기를 설정하는 경우에만 버퍼 크기 증가를 트리거합니다. 초기 버퍼 크기를 10으로 설정하는 경우 `Console.WriteLine` 문은 버퍼 크기 증가의 원인과 영향을 보여 줍니다. 4KB 초기 버퍼 크기에서 전체 샘플 JSON은 각 `Console.WriteLine`마다 표시되며 버퍼 크기를 늘릴 필요가 없습니다.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

앞의 예제에서는 버퍼 크기를 늘릴 수 있는 크기 제한을 설정하지 않습니다. 토큰 크기가 너무 클 경우 코드는 <xref:System.OutOfMemoryException> 예외와 함께 실패할 수 있습니다. 이 문제는 JSON이 크기가 약 1GB 이상인 토큰을 포함하는 경우 발생할 수 있습니다. 1GB 크기가 두 배가 되면 `int32` 버퍼에 비해 너무 커지기 때문입니다.

## <a name="additional-resources"></a>추가 자료

* [System.Text.Json 개요](system-text-json-overview.md)
* [사용자 지정 변환기를 작성하는 방법](system-text-json-converters-how-to.md)
* [Newtonsoft.Json에서 마이그레이션하는 방법](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.Json의 DateTime 및 DateTimeOffset 지원](../datetime/system-text-json-support.md)
* [System.Text.Json API 참조](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->

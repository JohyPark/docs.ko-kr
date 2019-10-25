---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393958"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="b844d-101">SignalR: HandshakeProtocol.SuccessHandshakeData가 대체됨</span><span class="sxs-lookup"><span data-stu-id="b844d-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="b844d-102">[HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) 필드가 제거되었으며 특정 `IHubProtocol`에 제공된 성공적인 핸드셰이크 응답을 생성하는 도우미 메서드로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="b844d-103">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="b844d-103">Version introduced</span></span>

<span data-ttu-id="b844d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b844d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b844d-105">이전 동작</span><span class="sxs-lookup"><span data-stu-id="b844d-105">Old behavior</span></span>

<span data-ttu-id="b844d-106">`HandshakeProtocol.SuccessHandshakeData`는 `public static ReadOnlyMemory<byte>` 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b844d-107">새 동작</span><span class="sxs-lookup"><span data-stu-id="b844d-107">New behavior</span></span>

<span data-ttu-id="b844d-108">`HandshakeProtocol.SuccessHandshakeData`는 지정된 프로토콜을 기반으로 `ReadOnlyMemory<byte>`를 반환하는 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 메서드로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span> 

#### <a name="reason-for-change"></a><span data-ttu-id="b844d-109">변경 이유</span><span class="sxs-lookup"><span data-stu-id="b844d-109">Reason for change</span></span>

<span data-ttu-id="b844d-110">비상수이며 선택된 프로토콜에 따라 변경되는 추가 필드가 핸드셰이크 _응답_에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b844d-111">권장 작업</span><span class="sxs-lookup"><span data-stu-id="b844d-111">Recommended action</span></span>

<span data-ttu-id="b844d-112">없음</span><span class="sxs-lookup"><span data-stu-id="b844d-112">None.</span></span> <span data-ttu-id="b844d-113">이 형식은 사용자 코드에서 사용하도록 설계되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="b844d-114">`public`이기 때문에 SignalR 서버와 클라이언트 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="b844d-115">.NET으로 작성된 고객 SignalR 클라이언트에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="b844d-116">SignalR의 **사용자**는 이 변경 내용의 영향을 받지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b844d-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="b844d-117">범주</span><span class="sxs-lookup"><span data-stu-id="b844d-117">Category</span></span>

<span data-ttu-id="b844d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b844d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b844d-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="b844d-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
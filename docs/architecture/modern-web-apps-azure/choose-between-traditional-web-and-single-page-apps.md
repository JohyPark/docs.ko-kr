---
title: 기존 웹앱 및 단일 페이지 앱 중에서 선택
description: 웹 애플리케이션을 구축하는 경우 기존 웹 앱과 SPA(단일 페이지 애플리케이션) 중에서 선택하는 방법을 알아봅니다.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d68c167dce791a31eeb5ca5729b50ec22c64f9b0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675480"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="3fc23-103">기존 웹앱 및 SPA(단일 페이지 앱) 중에서 선택</span><span class="sxs-lookup"><span data-stu-id="3fc23-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="3fc23-104">"Atwood의 법칙: JavaScript로 작성할 수 있는 모든 애플리케이션은 결국 JavaScript로 작성됩니다."</span><span class="sxs-lookup"><span data-stu-id="3fc23-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="3fc23-105">_\- Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="3fc23-105">_\- Jeff Atwood_</span></span>

<span data-ttu-id="3fc23-106">오늘날 웹 애플리케이션을 빌드하는 방법은 일반적으로 두 가지가 있습니다. 서버에서 대부분의 애플리케이션 논리를 수행하는 기존 웹 애플리케이션과 웹 브라우저에서 대부분의 사용자 인터페이스 논리를 수행하며 기본적으로 웹 API를 사용하여 웹 서버와 통신하는 SPA(단일 페이지 애플리케이션)가 바로 그것입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-106">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="3fc23-107">혼합 방식도 가능합니다. 가장 간단한 방법은 더 큰 기존 웹 애플리케이션 내에서 하나 이상의 풍부한 SPA와 같은 하위 애플리케이션을 호스트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-107">A hybrid approach is also possible, the simplest being host one or more rich SPA-like sub-applications within a larger traditional web application.</span></span>

<span data-ttu-id="3fc23-108">다음과 같은 경우 기존 웹 애플리케이션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-108">You should use traditional web applications when:</span></span>

- <span data-ttu-id="3fc23-109">애플리케이션의 클라이언트 쪽 요구 사항이 단순하거나 읽기 전용인 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-109">Your application's client-side requirements are simple or even read-only.</span></span>

- <span data-ttu-id="3fc23-110">JavaScript를 지원하지 않는 브라우저에서 애플리케이션이 작동해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-110">Your application needs to function in browsers without JavaScript support.</span></span>

- <span data-ttu-id="3fc23-111">팀이 JavaScript 또는 TypeScript 개발 기술에 익숙하지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-111">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="3fc23-112">다음과 같은 경우 SPA를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-112">You should use a SPA when:</span></span>

- <span data-ttu-id="3fc23-113">애플리케이션이 다양한 기능을 갖춘 풍부한 사용자 인터페이스를 노출해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-113">Your application must expose a rich user interface with many features.</span></span>

- <span data-ttu-id="3fc23-114">팀이 JavaScript 및/또는 TypeScript 개발에 익숙한 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-114">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

- <span data-ttu-id="3fc23-115">애플리케이션이 다른(내부 또는 공용) 클라이언트용 API를 이미 노출해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-115">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="3fc23-116">또한 SPA 프레임워크에는 보다 큰 아키텍처 및 보안 전문 지식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-116">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="3fc23-117">기존 웹 애플리케이션보다 잦은 업데이트 및 새 프레임워크로 인한 큰 변동이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-117">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="3fc23-118">자동화된 빌드 및 배포 프로세스를 구성하고 컨테이너와 같은 배포 옵션을 활용하는 방법은 기존 웹앱보다 SPA 애플리케이션이 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-118">Configuring automated build and deployment processes and utilizing deployment options like containers are more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="3fc23-119">SPA 모델 덕분에 향상된 사용자 경험을 이러한 고려 사항과 비교해서 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-119">Improvements in user experience made possible by SPA model must be weighed against these considerations.</span></span>

## <a name="blazor"></a><span data-ttu-id="3fc23-120">Blazor</span><span class="sxs-lookup"><span data-stu-id="3fc23-120">Blazor</span></span>

<span data-ttu-id="3fc23-121">ASP.NET Core 3.0에서는 Blazor라는 풍부하고 구성 가능한 대화형 UI를 빌드하는 새 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-121">ASP.NET Core 3.0 introduces a new model for building rich, interactive, and composable UI called Blazor.</span></span> <span data-ttu-id="3fc23-122">서버 측 Blazor를 사용하면 개발자가 서버에서 Razor를 사용하여 UI를 빌드하고, 이 코드를 브라우저에 전달하여 WebAssembly라는 JavaScript 라이브러리를 사용하여 클라이언트 쪽에서 실행되게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-122">Blazor server-side allows developers to build UI with Razor on the server and for this code to be delivered to the browser and executed client-side using a JavaScript library called WebAssembly.</span></span> <span data-ttu-id="3fc23-123">ASP.NET Core 3.0은 아직 개발 중이지만 이 eBook의 3.0 업데이트에서 이 기술에 대해 자세히 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-123">ASP.NET Core 3.0 is still under development, but you should expect to see more on this technology in the 3.0 update to this e-book.</span></span> <span data-ttu-id="3fc23-124">Blazor에 대한 자세한 내용은 [Blazor 시작](https://blazor.net/docs/get-started.html)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3fc23-124">For more information about Blazor, see [Get started with Blazor](https://blazor.net/docs/get-started.html).</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="3fc23-125">기존 웹앱을 선택하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-125">When to choose traditional web apps</span></span>

<span data-ttu-id="3fc23-126">다음에서는 이전에 설명한 기존 웹 애플리케이션을 선택해야 하는 이유를 좀 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-126">The following is a more detailed explanation of the previously stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="3fc23-127">**애플리케이션에 간단한 읽기 전용 클라이언트 쪽 요구 사항이 있는 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-127">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="3fc23-128">많은 웹 애플리케이션은 대부분의 사용자에게 주로 읽기 전용 방식으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-128">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="3fc23-129">읽기 전용(또는 대부분 읽기 전용인) 애플리케이션은 다양한 상태를 유지하고 조작하는 애플리케이션보다 훨씬 더 간단한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-129">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="3fc23-130">예를 들어 검색 엔진은 텍스트 상자가 있는 단일 진입점과 검색 결과를 표시하는 두 번째 페이지로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-130">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="3fc23-131">익명 사용자가 손쉽게 요청을 수행할 수 있으며 클라이언트 쪽 논리가 거의 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-131">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="3fc23-132">마찬가지로, 블로그 또는 콘텐츠 관리 시스템의 공용 애플리케이션은 일반적으로 클라이언트 쪽 동작이 거의 없는 콘텐츠로 주로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-132">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="3fc23-133">이러한 애플리케이션은 웹 서버에서 논리를 수행하고 브라우저에 표시되는 HTML을 렌더링하는 기존 서버 기반 웹 애플리케이션으로 손쉽게 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-133">Such applications are easily built as traditional server-based web applications which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="3fc23-134">사이트의 각 고유 페이지에 검색 엔진에서 책갈피에 추가하고 인덱싱할 수 있는 자체 URL이 있다는 사실(기본적으로 이를 애플리케이션의 별도 기능으로 추가할 필요 없음)은 이러한 시나리오에서 분명한 이점으로 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-134">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="3fc23-135">**JavaScript를 지원하지 않는 브라우저에서 애플리케이션이 작동해야 하는 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-135">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="3fc23-136">JavaScript 지원이 제한적이거나 없는 브라우저에서 작동해야 하는 웹 애플리케이션은 기존 웹앱 워크플로를 사용하여 작성해야 합니다(또는 최소한 이러한 동작으로 대체할 수 있어야 함).</span><span class="sxs-lookup"><span data-stu-id="3fc23-136">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="3fc23-137">SPA가 작동하려면 클라이언트 쪽 JavaScript가 필요합니다. 사용할 수 없다면 SPA가 좋은 선택이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-137">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="3fc23-138">**팀이 JavaScript 또는 TypeScript 개발 기술에 익숙하지 않은 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-138">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="3fc23-139">팀이 JavaScript 또는 TypeScript에 익숙하지 않지만 서버 쪽 웹 애플리케이션 개발에 익숙하다면 기존 웹앱을 SPA보다 더 빨리 제공할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-139">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="3fc23-140">SPA를 프로그래밍하는 방법을 배우는 것이 목표이거나 SPA가 제공하는 사용자 경험이 필요한 경우가 아니라면 기존 웹앱 빌드가 이미 익숙한 팀에게 기존 웹앱은 더 생산적인 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-140">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="3fc23-141">SPA를 선택하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc23-141">When to choose SPAs</span></span>

<span data-ttu-id="3fc23-142">다음은 웹앱 개발의 단일 페이지 애플리케이션 스타일을 선택하는 경우에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-142">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="3fc23-143">**애플리케이션이 다양한 기능을 갖춘 풍부한 사용자 인터페이스를 노출해야 하는 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-143">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="3fc23-144">SPA는 사용자가 작업을 수행하거나 앱의 영역 간에 이동할 때 페이지를 다시 로드할 필요가 없는 다양한 클라이언트 쪽 기능을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-144">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="3fc23-145">SPA는 백그라운드에서 데이터를 페치해서 더 빨리 로드할 수 있으며, 전체 페이지를 다시 로드하는 경우가 드물기 때문에 개별 사용자 작업의 반응성이 더욱 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-145">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="3fc23-146">SPA는 사용자가 단추를 클릭하여 양식을 제출할 필요 없이 부분적으로 완료된 양식이나 문서를 저장하는 증분 업데이트를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-146">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="3fc23-147">SPA는 끌어서 놓기와 같은 다양한 클라이언트 쪽 동작을 기존 애플리케이션보다 훨씬 쉽게 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-147">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="3fc23-148">SPA는 연결이 끊긴 모드에서 실행되도록 설계할 수 있습니다. 그러면 연결이 다시 설정된 후 클라이언트 쪽 모델이 업데이트되어 결국 서버로 다시 동기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-148">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="3fc23-149">앱의 요구 사항에 일반적인 HTML 형식이 제공하는 것 이상의 다양한 기능을 포함된 경우, SPA 스타일 애플리케이션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-149">You should choose a SPA style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="3fc23-150">SPA는 주소 표시줄에 의미 있는 URL을 표시하여 현재 작업을 반영하고 사용자가 이 URL을 책갈피에 추가하거나 딥 링크하여 돌아가도록 허용하는 등 기존 웹앱에 빌드된 기능을 구현해야 하는 경우가 자주 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-150">Note that frequently SPAs need to implement features that are built-in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="3fc23-151">또한 SPA는 사용자가 결과 페이지에서 브라우저의 뒤로 및 앞으로 단추를 사용할 수 있게 하여 당황하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-151">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="3fc23-152">**팀이 JavaScript 및/또는 TypeScript 개발에 익숙한 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-152">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="3fc23-153">SPA를 작성하려면 JavaScript 및/또는 TypeScript와 클라이언트 쪽 프로그래밍 기술 및 라이브러리에 익숙해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-153">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="3fc23-154">팀은 Angular와 같은 SPA 프레임워크를 사용하여 최신 JavaScript를 작성하는 데 능숙해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-154">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="3fc23-155">참조 - SPA 프레임워크</span><span class="sxs-lookup"><span data-stu-id="3fc23-155">References – SPA Frameworks</span></span>
>
> - <span data-ttu-id="3fc23-156">**Angular**</span><span class="sxs-lookup"><span data-stu-id="3fc23-156">**Angular**</span></span>  
>   <https://angular.io>
> - <span data-ttu-id="3fc23-157">**JavaScript 프레임워크 비교**</span><span class="sxs-lookup"><span data-stu-id="3fc23-157">**Comparison of JavaScript Frameworks**</span></span>  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

<span data-ttu-id="3fc23-158">**애플리케이션이 다른(내부 또는 공용) 클라이언트용 API를 이미 노출해야 하는 경우**</span><span class="sxs-lookup"><span data-stu-id="3fc23-158">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="3fc23-159">다른 클라이언트에서 사용할 웹 API가 이미 지원되는 경우, 서버 쪽 양식의 논리를 재현하는 대신 이러한 API를 활용하는 SPA 구현을 만드는 데 필요한 노력이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-159">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="3fc23-160">SPA는 사용자가 애플리케이션과 상호 작용할 때 웹 API를 광범위하게 사용하여 데이터를 쿼리하고 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-160">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="decision-table--traditional-web-or-spa"></a><span data-ttu-id="3fc23-161">의사 결정 테이블 – 기존 웹 또는 SPA</span><span class="sxs-lookup"><span data-stu-id="3fc23-161">Decision table – Traditional Web or SPA</span></span>

<span data-ttu-id="3fc23-162">다음 의사 결정 테이블에는 기존 웹 애플리케이션과 SPA 중에 하나를 선택할 때 고려해야 할 기본 요소 몇 가지가 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc23-162">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application and a SPA.</span></span>

| <span data-ttu-id="3fc23-163">**요소**</span><span class="sxs-lookup"><span data-stu-id="3fc23-163">**Factor**</span></span>                                           | <span data-ttu-id="3fc23-164">**기존 웹앱**</span><span class="sxs-lookup"><span data-stu-id="3fc23-164">**Traditional Web App**</span></span> | <span data-ttu-id="3fc23-165">**단일 페이지 애플리케이션**</span><span class="sxs-lookup"><span data-stu-id="3fc23-165">**Single Page Application**</span></span> |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| <span data-ttu-id="3fc23-166">팀의 JavaScript/TypeScript 숙련도 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3fc23-166">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="3fc23-167">**최소**</span><span class="sxs-lookup"><span data-stu-id="3fc23-167">**Minimal**</span></span>             | <span data-ttu-id="3fc23-168">**필수**</span><span class="sxs-lookup"><span data-stu-id="3fc23-168">**Required**</span></span>                |
| <span data-ttu-id="3fc23-169">스크립팅 없이 브라우저 지원</span><span class="sxs-lookup"><span data-stu-id="3fc23-169">Support Browsers without Scripting</span></span>                   | <span data-ttu-id="3fc23-170">**지원됨**</span><span class="sxs-lookup"><span data-stu-id="3fc23-170">**Supported**</span></span>           | <span data-ttu-id="3fc23-171">**지원 안 됨**</span><span class="sxs-lookup"><span data-stu-id="3fc23-171">**Not Supported**</span></span>           |
| <span data-ttu-id="3fc23-172">최소한의 클라이언트 쪽 애플리케이션 동작</span><span class="sxs-lookup"><span data-stu-id="3fc23-172">Minimal Client-Side Application Behavior</span></span>             | <span data-ttu-id="3fc23-173">**적합**</span><span class="sxs-lookup"><span data-stu-id="3fc23-173">**Well-Suited**</span></span>         | <span data-ttu-id="3fc23-174">**과도**</span><span class="sxs-lookup"><span data-stu-id="3fc23-174">**Overkill**</span></span>                |
| <span data-ttu-id="3fc23-175">다양하고 복잡한 사용자 인터페이스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3fc23-175">Rich, Complex User Interface Requirements</span></span>            | <span data-ttu-id="3fc23-176">**제한적**</span><span class="sxs-lookup"><span data-stu-id="3fc23-176">**Limited**</span></span>             | <span data-ttu-id="3fc23-177">**적합**</span><span class="sxs-lookup"><span data-stu-id="3fc23-177">**Well-Suited**</span></span>             |

>[!div class="step-by-step"]
><span data-ttu-id="3fc23-178">[이전](modern-web-applications-characteristics.md)
>[다음](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="3fc23-178">[Previous](modern-web-applications-characteristics.md)
[Next](architectural-principles.md)</span></span>
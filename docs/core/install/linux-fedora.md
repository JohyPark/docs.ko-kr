---
title: Fedora에 .NET Core 설치 - .NET Core
description: Fedora에 .NET Core SDK와 .NET Core 런타임을 설치하는 다양한 방법을 보여줍니다.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c90c08eefa074fa139642a268f879af79d7280da
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619483"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a>Fedora에 .NET Core SDK 또는 .NET Core 런타임 설치

.NET Core는 Fedora에서 지원됩니다. 이 문서에서는 Fedora에 .NET Core를 설치하는 방법을 설명합니다. Fedora 버전의 지원이 종료되면 해당 버전에서는 .NET Core도 더 이상 지원되지 않습니다. 그러나, 이러한 지침은 지원되지 않는 버전에서 .NET Core를 실행하는 데 도움이 될 수 있습니다.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>지원되는 배포

다음 표는 현재 지원되는 .NET Core 릴리스와 지원되는 Fedora 버전의 목록입니다. 이러한 버전은 각 버전의 [.NET Core가 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Fedora 버전이 지원 종료에 도달](https://fedoraproject.org/wiki/End_of_life)할 때까지 지원됩니다.

- ✔️는 Fedora 또는 .NET Core 버전이 계속 지원됨을 나타냅니다.
- ❌는 Fedora 또는 .NET Core 버전이 해당 Fedora 릴리스에서 지원되지 않음을 나타냅니다.
- Fedora 버전과 .NET Core 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 미리 보기(수동 설치만 해당) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 미리 보기 |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 미리 보기 |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 미리 보기 |
| ❌ [29](linux-fedora.md#fedora-29-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 미리 보기 |
| ❌ [28](linux-fedora.md#fedora-28-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 미리 보기 |
| ❌ [27](linux-fedora.md#fedora-27-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 미리 보기 |

다음 .NET Core 버전은 더 이상 지원되지 않습니다. 이러한 버전의 다운로드는 여전히 게시된 상태로 유지됩니다.

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>다른 버전을 설치하는 방법

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

.NET Core 3.1은 Fedora 32의 기본 패키지 리포지토리에서 사용할 수 있습니다.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>패키지 관리자 문제 해결

이 섹션에서는 패키지 관리자를 사용하여 .NET Core를 설치할 때 발생할 수 있는 일반적인 오류에 대한 정보를 제공합니다.

### <a name="failed-to-fetch"></a>가져오지 못함

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a>Snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>종속성

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>스크립팅된 설치

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>수동 설치

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>다음 단계

- [자습서: Visual Studio Code](../tutorials/with-visual-studio-code.md)를 사용하는 .NET Core SDK로 콘솔 애플리케이션 만들기

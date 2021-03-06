---
title: '방법: 인증서 지문 검색'
description: 인증을 위해 인증서를 사용 하는 WCF 응용 프로그램을 개발할 때 필요한 x.509 인증서에 있는 클레임을 지정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 87c696323af442021af267f0d8c523418e2234f7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246781"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>방법: 인증서 지문 검색
인증에 x.509 인증서를 사용 하는 WCF (Windows Communication Foundation) 응용 프로그램을 작성 하는 경우 인증서에 있는 클레임을 지정 해야 하는 경우가 많습니다. 예를 들어 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 메서드에 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 열거를 사용하는 경우 지문 클레임을 제공해야 합니다. 클레임 값을 찾는 과정은 두 단계로 이루어집니다. 첫째, 인증서에 대한 MMC(Microsoft Management Console) 스냅인을 엽니다. [방법: MMC 스냅인을 사용 하 여 인증서 보기](how-to-view-certificates-with-the-mmc-snap-in.md)를 참조 하세요. 두 번째는 여기에 설명 된 대로 적절 한 인증서를 찾고 해당 지문 (또는 기타 클레임 값)을 복사 합니다.  
  
 서비스 인증에 인증서를 사용하는 경우 **발급 대상** 열(콘솔의 첫 번째 열)의 값을 확인하는 것이 중요합니다. SSL(Secure Sockets Layer)을 전송 보안으로 사용하는 경우 수행되는 첫 번째 확인 작업 중 하나는 서비스의 기본 주소 URI(Uniform Resource Identifier)를 **발급 대상** 값과 비교하는 것입니다. 값이 일치해야 하며, 그렇지 않으면 인증 프로세스가 중지됩니다.  
  
 Powershell New-selfsignedcertificate cmdlet을 사용 하 여 개발 중에만 사용할 임시 인증서를 만들 수도 있습니다. 그러나 이러한 인증서는 기본적으로 인증 기관에서 발급 되지 않으며 프로덕션 용도로는 사용할 수 없습니다. 자세한 내용은 [방법: 개발 하는 동안 사용할 임시 인증서 만들기](how-to-create-temporary-certificates-for-use-during-development.md)를 참조 하세요.  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>인증서의 지문을 검색하려면  
  
1. 인증서에 대한 MMC(Microsoft Management Console) 스냅인을 엽니다. [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md)를 참조하세요.  
  
2. **콘솔 루트** 창의 왼쪽 창에서 **인증서(로컬 컴퓨터)** 를 클릭합니다.  
  
3. **개인** 폴더를 클릭하여 확장합니다.  
  
4. **인증서** 폴더를 클릭하여 확장합니다.  
  
5. 인증서 목록에서 **용도** 제목을 확인합니다. **클라이언트 인증** 을 용도로 표시하는 인증서를 찾습니다.  
  
6. 인증서를 두 번 클릭합니다.  
  
7. **인증서** 대화 상자에서 **자세히** 탭을 클릭합니다.  
  
8. 필드 목록을 스크롤하여 **지문**을 클릭합니다.  
  
9. 상자에서 16진수 문자를 복사합니다. `X509FindType`에 대한 코드에서 이 지문을 사용하는 경우 16진수 사이의 공백을 제거합니다. 예를 들어 지문 "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b"는 코드에서 "a909502dd82ae41433e6f83886b00d4277a32a7b"로 지정해야 합니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [방법: SSL 인증서를 사용하여 포트 구성](how-to-configure-a-port-with-an-ssl-certificate.md)
- [방법: MMC 스냅인을 사용하여 인증서 보기](how-to-view-certificates-with-the-mmc-snap-in.md)
- [방법: 개발 중에 사용할 임시 인증서 만들기](how-to-create-temporary-certificates-for-use-during-development.md)

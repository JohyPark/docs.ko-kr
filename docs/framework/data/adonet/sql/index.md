---
title: SQL Server 및 ADO.NET
description: 데이터베이스 관련 프로토콜을 캡슐화 하는 SQL Server에 대 한 .NET Framework Data Provider의 기능 및 동작에 대해 알아봅니다.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: eeb0ab69a68dfc2fc0faa1b4e833f80b307fffe5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286444"
---
# <a name="sql-server-and-adonet"></a>SQL Server 및 ADO.NET
이 단원에서는 .NET Framework Data Provider for SQL Server(<xref:System.Data.SqlClient>)와 관련된 기능 및 동작에 대해 설명합니다.  
  
 <xref:System.Data.SqlClient>는 데이터베이스 관련 프로토콜을 캡슐화하는 SQL Server 버전에 대한 액세스를 제공합니다. 이 데이터 공급자의 기능은 OLE DB, ODBC 및 Oracle용 .NET Framework 데이터 공급자와 유사하게 디자인되었습니다. <xref:System.Data.SqlClient>에는 SQL Server와 직접 통신하기 위한 TDS(Tabular Data Stream) 파서가 포함되어 있습니다.  
  
> [!NOTE]
> .NET Framework Data Provider for SQL Server를 사용하려면 애플리케이션에서 <xref:System.Data.SqlClient> 네임스페이스를 참조해야 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [SQL Server 보안](sql-server-security.md)  
 SQL Server 보안 기능에 대해 간략하게 설명하고 SQL Server를 대상으로 하는 안전한 ADO.NET 애플리케이션을 만드는 시나리오를 제공합니다.  
  
 [SQL Server 데이터 형식 및 ADO.NET](sql-server-data-types.md)  
 SQL Server 데이터 형식을 사용하는 방법 및 이러한 데이터 형식이 .NET Framework 데이터 형식과 상호 작용하는 방법에 대해 설명합니다.  
  
 [이진 및 대량 값 데이터 SQL Server](sql-server-binary-and-large-value-data.md)  
 SQL Server에서 큰 값 데이터를 사용하는 방법을 설명합니다.  
  
 [ADO.NET의 SQL Server 데이터 작업](sql-server-data-operations.md)  
 SQL Server에서 데이터를 사용하는 방법을 설명합니다. 대량 복사 작업, MARS, 비동기 작업 및 테이블 반환 매개 변수에 관한 섹션이 있습니다.  
  
 [SQL Server 기능 및 ADO.NET](sql-server-features-and-adonet.md)  
 ADO.NET 애플리케이션 개발자에게 유용한 SQL Server 기능에 대해 설명합니다.  
  
 [LINQ to SQL](./linq/index.md)  
 LINQ to SQL 애플리케이션을 만드는 데 필요한 기본 빌딩 블록, 프로세스 및 기술에 대해 설명합니다.  
  
 SQL Server 데이터베이스 엔진에 대한 자세한 내용은 사용 중인 SQL Server 버전에 해당하는 SQL Server 온라인 설명서를 참조하세요.  
  
 [SQL Server 온라인 설명서](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a>참고 항목

- [ADO.NET 애플리케이션 보안](../securing-ado-net-applications.md)
- [ADO.NET에서 데이터 형식 매핑](../data-type-mappings-in-ado-net.md)
- [DataSets, DataTables 및 DataViews](../dataset-datatable-dataview/index.md)
- [ADO.NET에서 데이터 검색 및 수정](../retrieving-and-modifying-data.md)
- [ADO.NET 개요](../ado-net-overview.md)

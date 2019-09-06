---
title: 資料來源物件介面
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311879"
---
# <a name="data-source-object-interfaces"></a>資料來源物件介面

下表顯示資料來源物件 OLE DB 所定義的必要和選擇性介面。

|介面|必要項？|由 OLE DB 範本來執行？|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|強制|是|
|`IDBInitialize`|強制|是|
|`IDBProperties`|強制|是|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|強制|是|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|選擇性|否|
|`IDBDataSourceAdmin`|選擇性|否|
|`IDBInfo`|選擇性|否|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|選擇性|否|
|`ISupportErrorInfo`|選擇性|否|

資料來源物件`IDBProperties`會透過繼承來`IDBInitialize`執行、 `IDBCreateSession`和介面。 您可以藉由繼承或不繼承自其中一個實作為類別，選擇支援其他功能。 如果您想要支援`IDBDataSourceAdmin`介面，您必須繼承`IDBDataSourceAdminImpl`自類別。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

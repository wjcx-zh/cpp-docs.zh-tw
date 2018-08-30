---
title: 資料來源物件介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25fca5e7e51789aceef8fb92cf48cc238a8e26fa
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195993"
---
# <a name="data-source-object-interfaces"></a>資料來源物件介面
下表定義由 OLE DB 資料來源物件的必要和選用的介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|強制|[是]|  
|`IDBInitialize`|強制|[是]|  
|`IDBProperties`|強制|[是]|  
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|強制|[是]|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|否|  
|`IDBDataSourceAdmin`|Optional|否|  
|`IDBInfo`|Optional|否|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Optional|否|  
|`ISupportErrorInfo`|Optional|否|  
  
 資料來源物件實作`IDBProperties`， `IDBInitialize`，和`IDBCreateSession`透過繼承的介面。 您可以選擇支援繼承或不繼承自其中一個實作類別的其他功能。 如果您想要支援`IDBDataSourceAdmin`介面，您必須繼承自`IDBDataSourceAdminImpl`類別。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
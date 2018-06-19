---
title: 資料來源物件介面 |Microsoft 文件
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
ms.openlocfilehash: 1c8aaed0a9f50e20dba5938b9b37425f4caa2bb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101873"
---
# <a name="data-source-object-interfaces"></a>資料來源物件介面
下表顯示由 OLE DB 資料來源物件定義的強制與選用介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|強制|[是]|  
|`IDBInitialize`|強制|[是]|  
|`IDBProperties`|強制|[是]|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|強制|[是]|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|否|  
|`IDBDataSourceAdmin`|Optional|否|  
|`IDBInfo`|Optional|否|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Optional|否|  
|`ISupportErrorInfo`|Optional|否|  
  
 資料來源物件實作`IDBProperties`， `IDBInitialize`，和`IDBCreateSession`透過繼承的介面。 您可以選擇支援繼承，或不繼承自其中一個實作類別的額外功能。 如果您想要支援`IDBDataSourceAdmin`介面，您必須繼承自`IDBDataSourceAdminImpl`類別。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
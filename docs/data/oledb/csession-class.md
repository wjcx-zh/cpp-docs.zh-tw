---
title: "CSession 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs: C++
helpviewer_keywords: CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d8b6bb75d12b4ab96c3a44c74f4487eb8a70efc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csession-class"></a>CSession 類別
代表單一資料庫存取工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
class CSession  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[中止](../../data/oledb/csession-abort.md)|取消 （終止） 交易。|  
|[關閉](../../data/oledb/csession-close.md)|關閉工作階段。|  
|[認可](../../data/oledb/csession-commit.md)|認可的交易。|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|傳回有關交易的資訊。|  
|[開啟](../../data/oledb/csession-open.md)|開啟資料來源物件的新工作階段。|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|開始新的交易，此工作階段。|  
  
## <a name="remarks"></a>備註  
 一或多個工作階段可由每個提供者連接 （資料來源） 與相關聯[CDataSource](../../data/oledb/cdatasource-class.md)物件。 若要建立新`CSession`如`CDataSource`，呼叫[csession:: Open](../../data/oledb/csession-open.md)。 若要開始資料庫交易，`CSession`提供`StartTransaction`方法。 一旦啟動交易，您可以在認可至使用**認可**方法，或取消使用**中止**方法。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CatDB](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
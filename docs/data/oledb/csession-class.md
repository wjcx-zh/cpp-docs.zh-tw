---
title: CSession 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs:
- C++
helpviewer_keywords:
- CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03c0bfec758bb663803b05b1f690816394f61239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="csession-class"></a>CSession 類別
代表單一資料庫存取工作階段。  
  
## <a name="syntax"></a>語法

```cpp
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
  
## <a name="see-also"></a>另請參閱  
 [CatDB](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
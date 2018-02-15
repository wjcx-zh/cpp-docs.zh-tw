---
title: "CSimpleRow 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c241118d13f7efecef9413851d3d47ff9a08b58
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="csimplerow-class"></a>CSimpleRow 類別
提供資料列控制代碼，使用中的預設實作[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)類別。  
  
## <a name="syntax"></a>語法

```cpp
class CSimpleRow  
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|將參考計數加入至現有的資料列控制代碼。|  
|[Compare](../../data/oledb/csimplerow-compare.md)|比較兩個資料列，以查看它們是否參考相同的資料列執行個體。|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|建構函式。|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|釋放資料列。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_dwRef](../../data/oledb/csimplerow-m-dwref.md)|現有的資料列控制代碼的參考計數。|  
|[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)|代表資料指標的資料列集的索引。|  
  
## <a name="remarks"></a>備註  
 資料列控制代碼邏輯上是唯一的標記的結果資料列。 `IRowsetImpl` 建立新`CSimpleRow`要求中的每個資料列[irowsetimpl:: Getnextrows](../../data/oledb/irowsetimpl-getnextrows.md)。 `CSimpleRow` 也可取代您自己的資料列控制代碼的實作的預設樣板引數，所以`IRowsetImpl`。 取代這個類別的唯一需求是能夠提供可接受類型的單一參數的建構函式取代類別**長**。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)
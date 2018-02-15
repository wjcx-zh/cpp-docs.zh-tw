---
title: "CEnumeratorAccessor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs:
- C++
helpviewer_keywords:
- CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57595cb2440aa8ad83c7cc0ad6916b3f22d6fb37
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor 類別
使用[CEnumerator](../../data/oledb/cenumerator-class.md)來存取資料列集列舉值的資料。  
  
## <a name="syntax"></a>語法

```cpp
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>成員  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|變數，指出列舉值是否為父列舉值，如果列舉值的資料列。|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|變數，表示資料列描述資料來源或列舉值。|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|列舉值之資料來源的描述。|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|列舉值之資料來源的名稱。|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|要傳遞至字串[IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604)取得 moniker，以便在資料來源或列舉值。|  
  
## <a name="remarks"></a>備註  
 此資料列集是由資料來源和顯示從目前的列舉值的列舉值所組成。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
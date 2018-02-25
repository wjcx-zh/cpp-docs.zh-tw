---
title: "CBookmark 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5c0f5f7a2af7c5b744fcad31ae6901988e92b9e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cbookmark-class"></a>CBookmark 類別
保存的書籤值在其緩衝區中。  
  
## <a name="syntax"></a>語法

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>參數  
 `nSize`  
 以位元組為單位的書籤緩衝區的大小。 當`nSize`是零，則在執行階段會以動態方式建立書籤緩衝區。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|建構函式|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|擷取緩衝區的指標。|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|擷取以位元組為單位的緩衝區大小。|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|設定書籤值。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](../../data/oledb/cbookmark-operator-equal.md)|會指派一個`CBookmark`到另一個類別。|  
  
## <a name="remarks"></a>備註  
 **CBookmark\<0 >**的樣板特製化`CBookmark`; 在執行階段動態建立其緩衝區。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
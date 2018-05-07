---
title: 'Crowset:: Compare |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>.Compare
- CRowset<TAccessor>::Compare
- ATL.CRowset<TAccessor>.Compare
- ATL::CRowset<TAccessor>::Compare
- CRowset.Compare
- ATL::CRowset::Compare
- ATL.CRowset.Compare
- CRowset::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 56e438e89cc41f124ea8678761d00d647d489466
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetcompare"></a>CRowset::Compare
比較兩個書籤使用[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Compare(const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *Bookmark1*  
 [in]要比較的第一個書籤。  
  
 *Bookmark2*  
 [in]要比較的第二個書籤。  
  
 `pComparison`  
 [out]指標比較的結果。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetLocate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetLocate**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
 使用書籤中取用者的相關資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)
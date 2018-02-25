---
title: CRowset::MoveLast | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CRowset<TAccessor>::MoveLast
- CRowset<TAccessor>::MoveLast
- ATL.CRowset.MoveLast
- ATL::CRowset::MoveLast
- CRowset<TAccessor>.MoveLast
- MoveLast
- CRowset::MoveLast
- ATL.CRowset<TAccessor>.MoveLast
- CRowset.MoveLast
dev_langs:
- C++
helpviewer_keywords:
- MoveLast method
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1657904b592c59b22a49c1fcaa3d55237a7bccf9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetmovelast"></a>CRowset::MoveLast
將游標移至最後一個資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveLast() throw();  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 呼叫[irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)重新定位下一個提取位置的最後一個位置，並擷取最後一個資料列。  
  
 這個方法會要求您設定**DBPROP_CANSCROLLBACKWARDS**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。 (為了達到最佳效能，您也可以設定**DBPROP_QUICKRESTART**至`VARIANT_TRUE`。)  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)
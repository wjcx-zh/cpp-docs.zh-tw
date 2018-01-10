---
title: "Crowset:: Movetobookmark |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs: C++
helpviewer_keywords: MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08e570d6d2cbc8c5943ce0591c280b74be573e2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
擷取書籤所標記的資料列或從該書籤位移至指定位置 (`lSkip`) 的資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT MoveToBookmark(   
   const CBookmarkBase& bookmark,   
   LONG lSkip = 0    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `bookmark`  
 [in] 標記您要從中擷取資料之位置的書籤。  
  
 `lSkip`  
 [in] 從書籤到目標資料列的資料列計數。 如果 `lSkip` 為零，將擷取的第一個資料列是已標記書籤的資料列。 如果 `lSkip` 為 1，將擷取的第一個資料列是已標記書籤的資料列之後的資料列。 如果`lSkip`為-1，將擷取的第一個資料列是已標記書籤的資料列之前的資料列。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetLocate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetLocate**至`VARIANT_TRUE`並設定**DBPROP_CANFETCHBACKWARDS**至`VARIANT_TRUE`之前先呼叫**開啟**資料表或命令包含資料列集。  
  
 使用書籤中取用者的相關資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [Crowset:: Movenext](../../data/oledb/crowset-movenext.md)   
 [Crowset:: Movefirst](../../data/oledb/crowset-movefirst.md)   
 [Irowsetlocate:: Getrowsat](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [Crowset:: Moveprev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)
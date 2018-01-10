---
title: "Crowset:: Movetoratio |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs: C++
helpviewer_keywords: MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 70b4d7994bb2175d0d402fdd309a8258f7127dc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
提取資料列從資料列集的小數位置開始。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT MoveToRatio(   
   DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,   
   bool bForward = true    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nNumerator`  
 [in]用來判斷小數分子位置要從中擷取資料。  
  
 `nDenominator`  
 [in]用來判斷小數分母位置要從中擷取資料。  
  
 `bForward`  
 [in]指出是否要向前或向後移動。 預設為向前復原。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 `MoveToRatio`提取資料列大約根據下列公式：  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 其中`RowsetSize`是以列數測量的資料列集的大小。 此公式的準確性，取決於特定的提供者。 如需詳細資訊，請參閱[irowsetscroll::](https://msdn.microsoft.com/en-us/library/ms709602.aspx)。  
  
 此方法需要的選擇性介面`IRowsetScroll`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetScroll**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)
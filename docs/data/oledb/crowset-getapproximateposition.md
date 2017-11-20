---
title: "Crowset:: Getapproximateposition |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::GetApproximatePosition
- ATL::CRowset<TAccessor>::GetApproximatePosition
- CRowset.GetApproximatePosition
- CRowset::GetApproximatePosition
- GetApproximatePosition
- ATL.CRowset.GetApproximatePosition
- CRowset<TAccessor>::GetApproximatePosition
dev_langs: C++
helpviewer_keywords: GetApproximatePosition method
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165537f3b61120237e7bfb8330ecf353bc01a107
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetapproximateposition"></a>CRowset::GetApproximatePosition
傳回對應至書籤的資料列的大約位置。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `pBookmark`  
 [in]識別要尋找其位置的資料列的書籤指標。 **NULL**只有資料列計數是必要項。  
  
 *pPosition*  
 [out]位置指標，其中`GetApproximatePosition`傳回資料列的位置。 **NULL**如果位置不需要。  
  
 `pcRows`  
 [out]位置指標，其中`GetApproximatePosition`傳回的資料列總數。 **NULL**如果不需要的資料列計數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetScroll`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetScroll**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
 使用書籤中取用者的相關資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)
---
title: "Cbookmark:: Setbookmark |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
dev_langs: C++
helpviewer_keywords: SetBookmark method
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d30e21724bb7ee0d9d2bf7a6a5a094390fff645a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cbookmarksetbookmark"></a>CBookmark::SetBookmark
複製所參考的書籤值`pBuffer`至`CBookmark`緩衝和緩衝區大小設定為`nSize`。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *nSize*  
 [in]書籤緩衝區的大小。  
  
 `pBuffer`  
 [in]包含書籤值的位元組陣列指標。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此函式僅供以**CBookmark\<0 >**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)
---
title: "Cdc:: setabortproc 的回呼函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::SetAbortProc
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::SetAbortProc
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1ba16ea60d8b18abd1962ded2da7e11ff2ef09a1
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcsetabortproc"></a>CDC::SetAbortProc 的回呼函式
名稱*AbortFunc*是應用程式提供的函式名稱的預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
#### <a name="parameters"></a>參數  
 *hPr*  
 識別的裝置內容。  
  
 `code`  
 指定是否已發生錯誤。 如果沒有發生任何錯誤，它會為 0。 它是**SP_OUTOFDISK**如果列印管理員正在磁碟空間不足，而且會使用應用程式會等候更多磁碟空間。 如果`code`是**SP_OUTOFDISK**，應用程式沒有中止列印工作。 如果不存在，它必須藉由呼叫產生列印管理員**PeekMessage**或**GetMessage** Windows 函式。  
  
## <a name="return-value"></a>傳回值  
 中止處理常式函式的傳回值，而且若要繼續，列印工作是否為非零 0 如果遭到取消。  
  
## <a name="remarks"></a>備註  
 必須輸出實際的名稱，如 < 備註 > 一節中所述[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)



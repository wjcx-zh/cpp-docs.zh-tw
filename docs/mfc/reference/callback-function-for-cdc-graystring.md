---
title: "Cdc:: graystring 的回呼函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::GrayString
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::GrayString
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
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
ms.openlocfilehash: 3ce3afefae9618420a8a97b27994c33604745677
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcgraystring"></a>CDC::GrayString 的回呼函式
*OutputFunc*是應用程式所提供的回呼函式名稱的預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
#### <a name="parameters"></a>參數  
 `hDC`  
 識別記憶體裝置內容的最少的點陣圖的寬度和高度所指定`nWidth`和`nHeight`到`GrayString`。  
  
 `lpData`  
 指向要繪製的字元字串。  
  
 `nCount`  
 指定要輸出的字元數。  
  
## <a name="return-value"></a>傳回值  
 回呼函式的傳回值必須是**TRUE**表示成功，否則就是**FALSE**。  
  
## <a name="remarks"></a>備註  
 回呼函式 (*OutputFunc*) 必須繪製影像的相對座標 (0，0) 而非 (*x*， *y*)。  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)



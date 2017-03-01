---
title: "Cdc:: enumobjects 的回呼函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::EnumObjects
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::EnumObjects
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
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
ms.openlocfilehash: e4b24b5f5333d5514b9fdf69d204bca5d7947d7a
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcenumobjects"></a>CDC::EnumObjects 的回呼函式
*ObjectFunc*名稱是應用程式提供的函式名稱的預留位置。  
  
## <a name="syntax"></a>語法  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
#### <a name="parameters"></a>參數  
 *lpszLogObject*  
 指向[LOGPEN](../../mfc/reference/logpen-structure.md)或[LOGBRUSH](../../mfc/reference/logbrush-structure.md)資料結構，包含物件的邏輯屬性相關資訊。  
  
 `lpData`  
 指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。  
  
## <a name="return-value"></a>傳回值  
 回呼函式會傳回 `int`。 這個傳回的值是使用者定義的。 如果回呼函式傳回 0，`EnumObjects` 會及早停止列舉。  
  
## <a name="remarks"></a>備註  
 必須輸出實際的名稱。  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)



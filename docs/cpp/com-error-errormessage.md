---
title: "_com_error::ErrorMessage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
- _com_error.ErrorMessage
- ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 01f244a07e46c70cbd4810af666f55dc899e5c3a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Microsoft 特定的**  
  
 擷取儲存在 `HRESULT` 物件中之 `_com_error` 的字串訊息。  
  
## <a name="syntax"></a>語法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回記錄在 `HRESULT` 物件中之 `_com_error` 的字串訊息。 如果`HRESULT`是對應的 16 位元[wCode](../cpp/com-error-wcode.md)，然後一般訊息 「`IDispatch error #<wCode>`"會傳回。 如果找不到訊息，則會傳回一般訊息「`Unknown error #<hresult>`」。 傳回的字串是 Unicode 或多位元組字串，根據的狀態**_UNICODE**巨集。  
  
## <a name="remarks"></a>備註  
 擷取記錄在 `HRESULT` 物件中之 `_com_error` 的適當系統訊息文字。 系統訊息文字透過呼叫 Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函式。 傳回的字串會由 `FormatMessage` API 配置，並且在終結 `_com_error` 物件時釋放。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)

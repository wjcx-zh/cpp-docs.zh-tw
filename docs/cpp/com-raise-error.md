---
title: _com_raise_error | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71a4be4ebf6029d0573aee71d74bf9faa241319f
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="comraiseerror"></a>_com_raise_error
**Microsoft 特定的**  
  
 擲回[_com_error](../cpp/com-error-class.md)以回應失敗。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 **IErrorInfo**物件。  
  
## <a name="remarks"></a>備註  
 `_com_raise_error`定義於\<comdef.h >，可由相同的名稱和原型的使用者撰寫版本取代。 如果您要使用 `#import`，但是不想要使用 C++ 例外狀況處理，則可以這樣做。 在此情況下，使用者版本**_com_raise_error**可能會決定要`longjmp`或顯示訊息方塊而停止。 不過，使用者版本不應傳回，因為編譯器 COM 支援程式碼不會預期它傳回。  
  
 您也可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)來取代預設錯誤處理函數。  
  
 根據預設，`_com_raise_error` 定義如下：  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** \<comdef.h >  
  
 **Lib:**如果**wchar_t 是原生類型**編譯器選項已開啟，請使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 是原生類型**已關閉，請使用 comsupp.lib。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [_set_com_error_handler](../cpp/set-com-error-handler.md)
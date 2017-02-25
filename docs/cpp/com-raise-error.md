---
title: "_com_raise_error | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_raise_error 函式"
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _com_raise_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擲回 [\_com\_error](../cpp/com-error-class.md) 以回應失敗。  
  
## 語法  
  
```  
  
      void __stdcall _com_raise_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = 0  
);  
```  
  
#### 參數  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 **IErrorInfo** 物件。  
  
## 備註  
 `_com_raise_error` 是在 comdef.h 中定義，可以取代為相同名稱和原型的使用者撰寫版本。  如果您要使用 `#import`，但是不想要使用 C\+\+ 例外狀況處理，則可以這樣做。  在這種情況下，使用者版本的 **\_com\_raise\_error** 可能會決定進行 `longjmp` 或顯示訊息方塊並暫止。  不過，使用者版本不應傳回，因為編譯器 COM 支援程式碼不會預期它傳回。  
  
 您也可以使用 [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md) 取代預設錯誤處理函式。  
  
 根據預設，`_com_raise_error` 定義如下：  
  
```  
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {  
   throw _com_error(hr, perrinfo);  
}  
```  
  
## END Microsoft 特定的  
  
## 需求  
 **標頭：**comdef.h  
  
 **Lib：**如果 \[wchar\_t 為原生類型\] 編譯器選項為開啟狀態，請使用 comsuppw.lib 或 comsuppwd.lib。  如果 \[wchar\_t 原生類型\] 為關閉狀態，請使用 comsupp.lib。  如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## 請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [\_set\_com\_error\_handler](../cpp/set-com-error-handler.md)
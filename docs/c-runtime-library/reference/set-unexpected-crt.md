---
title: "set_unexpected (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "set_unexpected"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_unexpected"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "例外狀況處理, 終止"
  - "set_unexpected 函式"
  - "unexpected 函式"
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_unexpected (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 `unexpected` 安裝終止函式。  
  
## 語法  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### 參數  
 `unexpFunction`  
 您要取代 `unexpected` 函式的函式的指標。  
  
## 傳回值  
 讓指標回到 `_set_unexpected` 註冊的前一個終止函式，讓先前函式可以還原。  如果先前函式未設定，則傳回值可用來還原預設行為;此值可能為 null。  
  
## 備註  
 `set_unexpected` 函式安裝 `unexpFunction` 做為 `unexpected`呼叫的函式。  `unexpected` 不實作於目前的 C\+\+ 例外狀況處理。  `unexpected_function` 型別以指向回傳 `void` 的使用者定義的 `unexpFunction` 函數的指標定義於 EH.H。  您的自訂 `unexpFunction` 函式不能傳回給其呼叫端。  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 根據預設， `unexpected` 會呼叫 `terminate`。  您可以撰寫自己的終止函式和以 `set_unexpected` 作為引數呼叫您的自訂的函式名稱函數以變更此預設行為。  `unexpected`會呼叫指定的最後一個函式做為 `set_unexpected` 的引數。  
  
 不同於以呼叫 `set_terminate` 安裝的自訂終止函式的，可以從 `unexpFunction` 中擲回例外狀況。  
  
 在多執行緒環境中，未預期的函式為每個執行緒分開維護。  每個新執行緒需要安裝它自己的未預期函式。  因此，每個執行緒負責自己的未預期處理。  
  
 於目前 Microsoft 實作 C\+\+ 例外狀況處理， `unexpected` 預設呼叫 `terminate` ，並不由例外狀況處理執行階段程式庫呼叫。  呼叫 `unexpected` 而非 `terminate` 沒有特殊好處。  
  
 所有動態連接的 DLL 或 EXE 具有單一 `set_unexpected` 處理常式;即使您呼叫 `set_unexpected` 您的處理常式可能由另一個取代或由另一個 DLL 或 EXE 集取代的處理常式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`set_unexpected`|\<eh.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)
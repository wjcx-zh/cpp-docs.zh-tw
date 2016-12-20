---
title: "longjmp | Microsoft Docs"
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
  - "longjmp"
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
  - "longjmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "longjmp 函式"
  - "還原堆疊環境和執行地區設定"
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# longjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

還原堆疊環境和執行地區設定。  
  
## 語法  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### 參數  
 `env`  
 儲存環境的變數。  
  
 *value*  
 要回傳予 `setjmp` 呼叫的值。  
  
## 備註  
 `longjmp` 函式於 `setjmp` 還原堆疊環境和先前儲存於 `env` 的執行地區設定。  `setjmp` 和 `longjmp` 提供一個執行非本地 `goto` 的方式。它們通常被用於傳遞執行控制予錯誤處理或還原之前被呼叫的常式的程式碼而不使用一般的呼叫與回傳慣例。  
  
 呼叫 `setjmp` 導致目前堆疊環境被儲存於 `env` 。  連續的 `longjmp` 呼叫還原已儲存的環境並回傳控制到對應的 `setjmp` 呼叫之下的點。  執行如同 *value* 剛被 `setjmp` 呼叫回傳般地繼續。  所有得到控制的常式的變數的值 \(除了暫存器變數\) 包含在呼叫 `longjmp` 時它們的值。  暫存器變數的值無法預期。  `setjmp` 回傳的值必須為非零。  如果 *value* 以 0 被傳遞，會實際以 1 為替代。  
  
 在呼叫 `setjmp` 的函式結束回傳前呼叫 `longjmp` 。否則結果會是無法預期的。  
  
 請觀察下列使用 `longjmp` 的限制：  
  
-   請勿假設暫存器變數的值會保持不變。  在呼叫 `setjmp` 的常式的暫存器變數的值可能不會在 `longjmp` 執行後被還原為適當的值。  
  
-   請勿使用 `longjmp` 來轉移中斷處理常式的控制，除非該中斷是由浮點例外狀況造成。  在此情況下，如果應用程式先透過呼叫 `_fpreset` 來重新初始化浮點數學套件，它可以由 `longjmp` 來從中斷處理常式結束回傳。  
  
     **注意** 請在 C\+\+ 應用程式裏小心地使用 `setjmp` 和 `longjmp` 。  因為這些函式並不支援 C\+\+ 物件語意，使用 C\+\+ 例外狀況處理機制是比較安全的。  
  
 如需詳細資訊，請參閱 [使用 setjmp 和 longjmp \(Using setjmp and longjmp\)](../../cpp/using-setjmp-longjmp.md) 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`longjmp`|\<setjmp.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 請參閱 [\_fpreset](../../c-runtime-library/reference/fpreset.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)
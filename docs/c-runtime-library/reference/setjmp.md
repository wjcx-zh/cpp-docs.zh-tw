---
title: "setjmp | Microsoft Docs"
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
  - "setjmp"
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
  - "setjmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "程式 [C++]，儲存狀態"
  - "目前狀態"
  - "setjmp 函式"
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

儲存程式的目前狀態。  
  
## 語法  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### 參數  
 `env`  
 儲存環境的變數。  
  
## 傳回值  
 在保存堆疊環境之後傳回 0 。  如果`setjmp`回傳呼叫`longjmp`的結果，則他會回傳`longjmp`的`value`引數，或是如果`longjmp`的`value`引數是0，則`setjmp`會回傳1。  不會回傳錯誤。  
  
## 備註  
 `setjmp` 函式儲存堆疊環境，您可以接著使用 `longjmp`以還原。  `setjmp 和`  `longjmp`一起使用時，可提供執行非區域 `goto` 的方式。  它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用一般呼叫或傳回慣例。  
  
 呼叫 `setjmp` 的方式儲存在 `env`的目前堆疊環境。  連續的 `longjmp` 呼叫還原已儲存的環境並回傳控制到對應的 `setjmp` 呼叫之下的點。  所有得到控制的常式的變數的值 \(除了暫存器變數\) 包含在呼叫 `longjmp` 時它們的值。  
  
 使用 `setjmp` 從原生程式碼跳到 Managed 程式碼是不可能的。  
  
 **注意事項** `setjmp` 和 `longjmp` 不支援 C\+\+ 物件語意。  在 C\+\+ 程式，請使用 C\+\+ 例外狀況處理機制。  
  
 如需詳細資訊，請參閱 [使用 setjmp 和 longjmp \(Using setjmp and longjmp\)](../../cpp/using-setjmp-longjmp.md) 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`setjmp`|\<setjmp.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_fpreset](../../c-runtime-library/reference/fpreset.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [\_setjmp3](../../c-runtime-library/setjmp3.md)
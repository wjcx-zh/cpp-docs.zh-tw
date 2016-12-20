---
title: "使用 setjmp/longjmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "longjmp"
  - "setjmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, setjmp/longjmp 函式"
  - "C++ 程式中的 longjmp 函式"
  - "setjmp 函式"
  - "setjmp 函式, C++ 程式"
  - "SETJMP.H"
  - "SETJMPEX.H"
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 setjmp/longjmp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[setjmp](../c-runtime-library/reference/setjmp.md) 和 [longjmp](../c-runtime-library/reference/longjmp.md) 一起使用時，可提供執行非區域 `goto` 的方式。  它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用標準呼叫或傳回慣例。  
  
> [!CAUTION]
>  不過，由於 `setjmp` 和 `longjmp` 不支援 C\+\+ 物件語意，而且它們可能會阻止區域變數最佳化而造成效能降低，因此建議您不要在 C\+\+ 程式中使用它們。  建議您改用 `try`\/`catch` 建構。  
  
 如果您決定在 C \+\+ 程式中使用 `setjmp`\/`longjmp`，請同時包括 SETJMP.H 或 SETJMPEX.H，以確保函式與 C\+\+ 例外狀況處理之間能正確互動。  如果您使用 [\/EH](../build/reference/eh-exception-handling-model.md) 進行編譯，則會在堆疊回溯期間呼叫本機物件的解構函式。  如果您使用 **\/EHs** 進行編譯，而其中一個函式呼叫使用 [nothrow](../cpp/nothrow-cpp.md) 的函式，而且使用 `nothrow` 的函式呼叫 `longjmp`，則根據最佳化程式而定，解構函式回溯可能不會發生。  
  
 在可攜式程式碼中，當執行呼叫 `longjmp` 的非本機 `goto` 時，畫面物件的正確解構可能不可靠。  
  
## 請參閱  
 [混合 C \(結構化\) 和 C\+\+ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)
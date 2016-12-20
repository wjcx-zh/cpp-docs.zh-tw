---
title: "在 __asm 區塊中使用 C 或 C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 其中的 C/C++ 元素"
  - "註解, 在 __asm 區塊中"
  - "常數, 在 __asm 區塊中"
  - "內嵌組譯碼, 混合指令與 C/C++ 陳述式"
  - "巨集, __asm 區塊"
  - "前置處理器指示詞"
  - "前置處理器指示詞, 在 __asm 區塊中使用"
  - "前置處理器, 指示詞"
  - "符號, 在 __asm 區塊中"
  - "類型名稱, 在 __asm 區塊中使用"
  - "typedef 名稱, 在 __asm 區塊中使用"
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 __asm 區塊中使用 C 或 C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 由於內嵌組譯碼指令可以與 C 或 C\+\+ 陳述式混用，因此它們可以依名稱參考 C 或 C\+\+ 變數，以及使用這些語言的許多其他項目。  
  
 `__asm` 區塊可以使用下列語言項目：  
  
-   符號，包括標籤及變數和函式名稱  
  
-   常數，包括符號常數和 `enum` 成員  
  
-   巨集和前置處理器指示詞  
  
-   註解 \(**\/\* \*\/** 和 **\/\/**\)  
  
-   類型名稱 \(MASM 類型為合法的任何位置\)  
  
-   `typedef` 名稱，通常搭配 **PTR** 和 **TYPE** 這類運算子使用，或用來指定結構或等位成員  
  
 在 `__asm` 區塊內，您可以使用 C 標記法或組合語言基數標記法 \(例如 0x100 和 100h 相等\) 指定整數常數。  這樣您就可以在 C 中定義常數 \(使用 `#define`\)，然後在 C 或 C\+\+ 中與程式的組合語言部分使用該常數。  您也可以在常數前面加上 0，指定八進位的常數。  例如，0777 會指定八進位常數。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [在 \_\_asm 區塊中使用運算子](../../assembler/inline/using-operators-in-asm-blocks.md)  
  
-   [在 \_\_asm 區塊中使用 C 或 C\+\+ 符號](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)  
  
-   [存取 \_\_asm 區塊中的 C 或 C\+\+ 資料](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)  
  
-   [使用內嵌組譯碼撰寫函式](../../assembler/inline/writing-functions-with-inline-assembly.md)  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)
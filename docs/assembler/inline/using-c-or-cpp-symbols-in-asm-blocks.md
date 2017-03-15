---
title: "在 __asm 區塊中使用 C 或 C++ 符號 | Microsoft Docs"
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
  - "__asm 關鍵字 [C++], 語法"
  - "符號, 在 __asm 區塊中"
  - "Visual C, __asm 區塊中的符號"
  - "Visual C++, 在 __asm 區塊中"
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 __asm 區塊中使用 C 或 C++ 符號
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 `__asm`區塊可以指向組塊 」 出現的位置的範圍中的任何 C 或 c \+ \+ 符號。  \(C 和 c \+ \+ 符號是變數名稱、 函式名稱和標籤。 也就是不是符號常數的名稱或`enum`成員。  您不能呼叫 c \+ \+ 成員函式。\)  
  
 使用 C 和 c \+ \+ 符號有一些限制：  
  
-   每個組件語言陳述式可以包含只有一個 C 或 c \+ \+ 符號。  多個符號可以出現在相同的組件指令，只能與**長度**， **型別**，和 **大小**的運算式。  
  
-   函式中參考`__asm`區塊必須宣告 \(原型\) 的程式中稍早。  否則，編譯器無法區別函式名稱和標籤`__asm`區塊。  
  
-   `__asm`區塊不能使用相同的拼字 \(不考慮大小寫\) 的 MASM 保留字做的任何 C 或 c \+ \+ 符號。  MASM 保留字包括指令名稱例如， **推入**與註冊 SI 這樣的名稱。  
  
-   結構和等位的標籤不能識別在`__asm`區塊。  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)
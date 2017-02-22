---
title: "將 __asm 區塊定義為 C 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 做為 C 巨集"
  - "巨集, __asm 區塊"
  - "Visual C, 巨集"
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 將 __asm 區塊定義為 C 巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 C 的巨集提供便利的方式將組譯程式碼插入程式碼中，但它們會要求額外進行處理，因為巨集展開成單一邏輯行。  若要建立簡單的巨集，請依照下列這些規則：  
  
-   括住`__asm`封鎖大括弧括住。  
  
-   將`__asm`在每個組件指令之前的關鍵字。  
  
-   使用舊式 C 註解 \(  `/* comment */`\) 而不是組件樣式註解 \(   `; comment`\) 或單行 C 註解 \(   `// comment`\)。  
  
 為了說明，下列範例會定義簡單的巨集：  
  
```  
#define PORTIO __asm      \  
/* Port output */         \  
{                         \  
   __asm mov al, 2        \  
   __asm mov dx, 0xD007   \  
   __asm out dx, al       \  
}  
```  
  
 第一眼看，其中最後三個`__asm`關鍵字起來好像多餘。  有需要，不過，因為巨集展開的單一行中：  
  
```  
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }  
```  
  
 第三個和第四個`__asm`關鍵字所需做為陳述式分隔符號。  在中辨識唯一的陳述式分隔符號`__asm`區塊是新行字元和  `__asm`關鍵字。  因為區塊定義為巨集是一個邏輯程式敘述行，您必須分隔與每個指示 `__asm`.  
  
 在大括號也很重要。  如果您省略它們，編譯器可以在同一行右邊的 \[巨集引動過程的 C 或 c \+ \+ 陳述式所混淆。  沒有右括號，編譯器無法分辨在組件程式碼會停止，而它看到 C 或 c \+ \+ 的陳述式`__asm`為組件的指令區塊。  
  
 以分號開頭的組件樣式註解 \(**;**\) 繼續至行結尾。  在巨集中中，因為編譯器會忽略所有項目之後的註解，一直到邏輯程式敘述行的結尾，這會造成問題。  單行 C 或 c \+ \+ 註解也是一樣 \(  `// comment`\)。  若要避免錯誤，請使用 \[舊式 C 註解 \(  `/* comment */`\) 在  `__asm`區塊定義為巨集。  
  
 `__asm`撰寫 C 巨集可以取得引數的區塊。  與一般 C 巨集，但是，不同的是`__asm`巨集無法傳回值。  因此您無法在 C 或 c \+ \+ 運算式中使用這類巨集。  
  
 請小心不要隨意叫用這種類型的巨集。  舉個例說，叫用一個組合語言的巨集函式中宣告的`__fastcall`慣例可能會造成未預期的結果。  \(請參閱[使用，並保留在內嵌組譯碼中的暫存器](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)。\)  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)
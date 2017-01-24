---
title: "檔案轉譯概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案轉譯 [C++], 關於檔案轉譯"
  - "檔案 [C++], 轉譯"
  - "前置處理轉譯階段"
  - "程式 [C++], 的語彙慣例"
  - "轉譯 [C++]"
  - "轉譯階段"
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檔案轉譯概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 程式 \(類似 C 程式\) 包含一個或多個檔案。  這些檔案都按下列概念順序轉譯 \(實際的順序會依循 "as if" 規則：如果已依照這些步驟進行，則必須進行轉譯\)：  
  
1.  語彙 Token 化。  此轉譯階段中會執行字元對應和三併詞處理、行接合，以及 Token 化。  
  
2.  前置處理。  這個轉譯階段會帶入 `#include` 指示詞所參考的附屬原始程式檔、處理「字串化」和「字元化」指示詞，並執行語彙基元帶入和巨集展開 \(如需詳細資訊，請參閱《前置處理器參考》中的[前置處理器指示詞](../preprocessor/preprocessor-directives.md)\)。  前置處理階段產生的結果是一個結合起來，定義一個「轉譯單位」的語彙基元序列。  
  
     前置處理器指示詞一律會以數字符號 \(**\#**\) 字元做為開頭 \(也就是該行的第一個非空白字元必須是數字符號\)。  指定行上只能有一個前置處理器指示詞。  例如：  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  程式碼產生。  這個轉譯階段會使用前置處理階段中產生的語彙基元來產生物件程式碼。  
  
     在這個階段中會執行原始程式碼的語法和語意檢查。  
  
 如需詳細資訊，請參閱《前置處理器參考》中的[轉譯階段](../preprocessor/phases-of-translation.md)。  
  
 C\+\+ 前置處理器是 ANSI C 語言前置處理器的嚴格超集，不過，C\+\+ 前置處理器在某些情況下有所不同。  下列清單說明 ANSI C 和 C\+\+ 前置處理器之間的一些差異：  
  
-   支援單行註解。  如需詳細資訊，請參閱[註解](../cpp/comments-cpp.md)。  
  
-   僅針對 C\+\+ 定義預先定義的巨集 **\_\_cplusplus**。  如需詳細資訊，請參閱《前置處理器參考》中的[預先定義的巨集](../preprocessor/predefined-macros.md)。  
  
-   C 前置處理器無法辨識 C\+\+ 運算子：**.\***、**–\>\*** 和 `::`。  如需運算子的詳細資訊，請參閱[運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)和[運算式](../cpp/expressions-cpp.md)。  
  
## 請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)
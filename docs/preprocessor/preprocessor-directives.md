---
title: "前置處理器指示詞 | Microsoft Docs"
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
  - "指示詞, 前置處理器"
  - "前置處理器, 指示詞"
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 前置處理器指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前置處理器指示詞 \(例如 `#define` 和 **\#ifdef**\) 通常用來使來源程式在不同的執行環境中易於變更和易於編譯。  原始程式檔中的指示詞會指示前置處理器執行特定動作。  例如，前置處理器可以取代文字中的語彙基元、將其他檔案的內容插入原始程式檔，或是透過移除文字區段來隱藏編譯檔案的一部分。  在巨集展開之前，會辨識並執行前置處理器程式行。  因此，如果巨集展開成類似前置處理器命令的程式碼，前置處理器就無法辨識該命令。  
  
 除了不支援逸出序列以外，前置處理器陳述式使用的字元集與原始程式檔陳述式使用的相同。  前置處理器陳述式中使用的字元集與[執行字元集](http://msdn.microsoft.com/zh-tw/a7901c61-524d-47c6-beb6-d9dacc2e72ed)相同。  前置處理器也會辨識負數字元值。  
  
 前置處理器會辨識下列指示詞：  
  
|||||  
|-|-|-|-|  
|[\#define](../preprocessor/hash-define-directive-c-cpp.md)|[\#error](../preprocessor/hash-error-directive-c-cpp.md)|[\#import](../preprocessor/hash-import-directive-cpp.md)|[\#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[\#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#include](../preprocessor/hash-include-directive-c-cpp.md)|[\#using](../preprocessor/hash-using-directive-cpp.md)|  
|[\#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#line](../preprocessor/hash-line-directive-c-cpp.md)|[\#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[\#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 數字符號 \(**\#**\) 必須是包含指示詞之程式行的第一個非空白字元；空白字元可以出現在數字符號和指示詞的第一個字母之間。  某些指示詞會包含引數或值。  指示詞後面的所有文字 \(指示詞中的引數或值除外\) 前面必須有單行註解分隔符號 \(**\/\/**\) 或放在註解分隔符號 \(**\/\* \*\/**\) 之中。  包含前置處理器指示詞的程式行可以緊鄰行尾標記之前再加上反斜線 \(**\\**\) 來接續。  
  
 前置處理器指示詞可以出現在原始程式檔的任何位置，但是這只會套用至原始程式檔的其餘部分。  
  
## 請參閱  
 [前置處理器運算子](../preprocessor/preprocessor-operators.md)   
 [預先定義的巨集](../preprocessor/predefined-macros.md)   
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)
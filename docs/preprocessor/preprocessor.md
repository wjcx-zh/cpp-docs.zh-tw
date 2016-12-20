---
title: "前置處理器 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "前置處理器"
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 前置處理器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前置處理器是文字處理器，會在轉譯的第一個階段操作原始程式檔的文字。  前置處理器不會剖析原始程式文字，但會將原始程式文字分解為用於尋找巨集呼叫的語彙基元。  雖然編譯器通常在第一次傳遞時叫用前置處理器，但也可以分別叫用前置處理器，在不進行編譯的情況下處理文字。  
  
 有關前置處理器的參考資料包含下列章節：  
  
-   [前置處理器指示詞](../preprocessor/preprocessor-directives.md)  
  
-   [前置處理器運算子](../preprocessor/preprocessor-operators.md)  
  
-   [預先定義巨集](../preprocessor/predefined-macros.md)  
  
-   [Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
  
 **Microsoft 特定的**  
  
 您可以使用 [\/E](../build/reference/e-preprocess-to-stdout.md) 或 [\/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 編譯器選項，在前置處理之後取得原始程式碼的清單。  兩個選項均會叫用前置處理器，並將產生的文字輸出到標準輸出裝置 \(通常是主控台\)。  這兩個選項之間的差異是 \/E 包括 `#line` 指示詞，而 \/EP 則會刪除這些指示詞。  
  
 **END Microsoft 特定的**  
  
##  <a name="_predir_special_terminology"></a> 特殊術語  
 在前置處理器文件中，「引數」一詞是指傳遞至函式的實體。  某些情況下，會以「實際」或「型式」修飾「引數」一詞，分別用於說明函式呼叫中指定的引數運算式，以及函式定義中指定的引數宣告。  
  
 「變數」一詞是指簡單的 C 類型資料物件。  「物件」一詞是指 C\+\+ 物件和變數；屬於內含的詞彙。  
  
## 請參閱  
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)   
 [轉譯階段](../preprocessor/phases-of-translation.md)
---
title: "alloc_text | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.alloc_text"
  - "alloc_text_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "alloc_text pragma"
  - "Pragma, alloc_text"
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alloc_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為要放置指定之函式定義的程式碼區段命名。  pragma 必須在函式宣告子與具名函式的函式定義之間發生。  
  
## 語法  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## 備註  
 **alloc\_text** pragma 不會處理 C\+\+ 成員函式或多載函式。  它只適用於使用 C 連結宣告的函式，也就是以 **extern "C"** 連結規格宣告的函式。  如果您嘗試在使用 C\+\+ 連結的函式上使用這個 pragma，則會產生編譯器錯誤。  
  
 由於不支援使用 `__based` 的函式定址，因此指定區段位置需要使用 **alloc\_text** pragma。  *textsection* 所指定的名稱應該以雙引號括住。  
  
 **alloc\_text** pragma 必須出現在任何所指定函式的宣告之後，以及這些函式的定義之前。  
  
 **alloc\_text** pragma 中參考的函式應該與 pragma 在相同模組中定義。  如果沒有這樣做，而且之後將未定義的函式編譯為不同的文字區段，則不一定會攔截錯誤。  雖然程式通常會正確執行，但是函式不會配置在預定的區段中。  
  
 **alloc\_text** 的其他限制如下：  
  
-   不能在函式內部使用。  
  
-   使用時機必須是在函式宣告之後，但是在函式定義之前。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
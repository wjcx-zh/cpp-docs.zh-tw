---
title: "inline_recursion | Microsoft Docs"
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
  - "inline_recursion_CPP"
  - "vc-pragma.inline_recursion"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "inline_recursion pragma"
  - "Pragma, inline_recursion"
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# inline_recursion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制直接或相互遞迴函式呼叫的內嵌展開。  
  
## 語法  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## 備註  
 使用這個 pragma 控制標記為 [inline](../misc/inline-inline-forceinline.md) 和 [\_\_inline](../misc/inline-inline-forceinline.md) 的函式，或是編譯器會自動在 \/Ob2 選項底下展開的函式。  使用這個 pragma 必須搭配 [\/Ob](../build/reference/ob-inline-function-expansion.md) 編譯器選項設定 \(1 或 2\)。  `inline_recursion` 的預設狀態是關閉的。  這個 pragma 會在 pragma 出現後的第一個函式呼叫中生效，而且不會影響該函式的定義。  
  
 `inline_recursion` pragma 控制遞迴函式的展開方式。  如果 `inline_recursion` 已關閉，且內嵌函式呼叫其本身 \(直接或間接\)，則該函式只會展開一次。  如果 `inline_recursion` 已開啟，則該函式會展開多次，直到達到以 [inline\_depth](../preprocessor/inline-depth.md) pragma 設定的值 \(`inline_depth` pragma 定義之遞迴函式的預設值\) 或容量限制為止。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_depth](../preprocessor/inline-depth.md)   
 [\/Ob \(內嵌函式展開\)](../build/reference/ob-inline-function-expansion.md)
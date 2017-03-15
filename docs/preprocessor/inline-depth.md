---
title: "inline_depth | Microsoft Docs"
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
  - "inline_depth_CPP"
  - "vc-pragma.inline_depth"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "inline_depth pragma"
  - "Pragma, inline_depth"
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# inline_depth
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定內嵌啟發式搜尋深度，這樣一來，如果函式的深度 \(在呼叫圖形中\) 大於 `n`，就不會將該函式內嵌。  
  
## 語法  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## 備註  
 這個 pragma 會控制標記為 [inline](../misc/inline-inline-forceinline.md) 和 [\_\_inline](../misc/inline-inline-forceinline.md)，或是自動內嵌在 \/Ob2 選項底下之函式的內嵌行為。  
  
 `n` 可以是介於 0 和 255 之間的值，其中 255 表示在呼叫圖形中不限深度，而零則表示禁止內嵌展開。若未指定 `n`，則會使用預設值 \(254\)。  
  
 **inline\_depth** pragma 負責控制一系列函式呼叫能夠展開的次數。  例如，如果內嵌深度為四，而且 A 呼叫 B，然後 B 呼叫 C，則這三個呼叫將會以內嵌方式展開。  不過，如果最接近的內嵌展開為二，則只會展開 A 和 B，C 則保持為函式呼叫。  
  
 若要使用這個 pragma，您必須將 \/Ob 編譯器選項設定為 1 或 2。  使用這個 pragma 設定的深度會在 pragma 之後的第一次函式呼叫生效。  
  
 內嵌深度可以在展開期間減少，但是不能增加。  如果內嵌深度為六，而在展開期間前置處理器遇到值為八的 **inline\_depth**，則深度會保持為六。  
  
 **inline\_depth** pragma 對於標記為 `__forceinline` 的函式沒有作用。  
  
> [!NOTE]
>  遞迴函式可透過內嵌於最大 16 個呼叫深度的方式替代。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_recursion](../preprocessor/inline-recursion.md)
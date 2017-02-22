---
title: "迴圈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "loop_CPP"
  - "vc-pragma.loop"
dev_langs: 
  - "C++"
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 迴圈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制 auto\-parallelizer 考量迴圈程式碼的方式，及\/或從 auto\-vectorizer 排除迴圈的考量。  
  
## 語法  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### 參數  
 `hint_parallel(` `n` `)`  
 編譯器提示此迴圈應在 `n` 個執行緒之間進行平行處理，其中 `n` 為正整數或零。  如果 `n` 是零，則會在執行階段使用最大數目的執行緒。  這是提供給編譯器的提示，而不是一個命令，因此，並不保證迴圈會進行平行處理。  如果迴圈具有資料相依性或結構問題 \(例如，在迴圈主體之外使用純量的迴圈存放區\)，則不會對迴圈進行平行處理。  
  
 除非已指定 [\/Qpar](../build/reference/qpar-auto-parallelizer.md) 編譯器參數，否則編譯器會忽略這個選項。  
  
 `no_vector`  
 預設會開啟 auto\-vectorizer 並嘗試向量化其評估為可從中受益的所有迴圈。  指定這個 pragma 可針對後方的迴圈停用 auto\-vectorizer。  
  
 `ivdep`  
 編譯器的提示，忽略此迴圈的向量相依性。  請將它與 `hint_parallel` 搭配使用。  
  
## 備註  
 若要使用 `loop` pragma，請將它放在迴圈定義的前方 \(而不是內部\)。  pragma 生效範圍為其後方迴圈的範圍。  您可以任何順序對迴圈套用多個 pragma，不過，您必須在個別的 pragma 陳述式中加以說明。  
  
## 請參閱  
 [自動平行處理和自訂向量化](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
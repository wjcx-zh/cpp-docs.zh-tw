---
title: "#undef 指示詞 (C/C++) | Microsoft Docs"
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
  - "#undef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#undef 指示詞"
  - "前置處理器, 指示詞"
  - "undef 指示詞 (#undef)"
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #undef 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除 \(取消定義\) 先前使用 `#define` 建立的名稱。  
  
## 語法  
  
```  
  
#undef   
identifier  
  
```  
  
## 備註  
 `#undef` 指示詞會移除 *identifier* 目前的定義。  因此，前置處理器會忽略後續出現的 *identifier*。  若要使用 `#undef` 移除巨集定義，請只提供巨集 *identifier*，而不要提供參數清單。  
  
 您也可以將 `#undef` 指示詞套用至沒有先前定義的識別項。  這樣可確保識別項處於未定義狀態。  巨集取代不會在 `#undef` 陳述式內執行。  
  
 `#undef` 指示詞通常會與 `#define` 指示詞配對，以便在原始程式中建立識別項在其中具有特殊意義的區域。  例如，原始程式的特定函式可以使用資訊清單常數，以定義不會影響程式其他部分的環境特定值。  `#undef` 指示詞也可搭配 `#if` 指示詞，以控制原始程式的條件式編譯。  如需詳細資訊，請參閱 [\#if、\#elif、\#else 和 \#endif 指示詞](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
 在下列範例中，`#undef` 指示詞會移除符號常數和巨集的定義。  請注意，其中只會提供巨集的識別項。  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Microsoft 特定的**  
  
 您可以從命令列使用 \/U 選項，後面接著要取消定義的巨集名稱，藉此取消巨集的定義。  發出這個命令的作用相當於檔案開頭的 `#undef` *macro\-name* 陳述式序列。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)
---
title: "編譯器警告 (層級 1) C4129 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4129"
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'character' : 無法辨識的字元逸出序列  
  
 跟在字元或字串常數的反斜線 \(\\\) 後的 `character`，無法辨識成有效的逸出序列 \(Escape Sequence\)。  此反斜線會被忽略，且不進行列印。  反斜線之後的字元會被列印。  
  
 若要列印單一反斜線，請指定雙反斜線 \(\\\\\)。  
  
 C\+\+ 標準，在 2.13.2 一節中會討論逸出序列。  
  
 下列範例會產生 C4129：  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```
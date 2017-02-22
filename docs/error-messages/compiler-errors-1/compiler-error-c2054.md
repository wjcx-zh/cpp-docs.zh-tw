---
title: "編譯器錯誤 C2054 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2054"
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 'identifier' 之後必須是 '\('  
  
 函式識別項被用在後面需要括弧的內容中。  
  
 這項錯誤可能會因為在複雜初始設定上省略等號 \(\=\) 而產生。  
  
 下列範例會產生 C2054：  
  
```  
// C2054.c  
int array1[] { 1, 2, 3 };   // C2054, missing =  
```  
  
 可能的解決方案：  
  
```  
// C2054b.c  
int main() {  
   int array2[] = { 1, 2, 3 };  
}  
```
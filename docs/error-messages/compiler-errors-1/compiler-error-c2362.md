---
title: "編譯器錯誤 C2362 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2362"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2362"
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2362
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' 的初始化已由 'goto label' 略過  
  
 在以 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 編譯時，跳到某標記將導致識別項無法進行初始化。  
  
 您不能跳過包含初始設定式的宣告，除非該宣告包含在不會進入的區塊內，或是變數已經被初始化。  
  
 下列範例會產生 C2326：  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 可能的解決方案：  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```
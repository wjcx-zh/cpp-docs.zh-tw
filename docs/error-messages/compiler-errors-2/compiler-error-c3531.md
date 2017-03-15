---
title: "編譯器錯誤 C3531 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3531"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3531"
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3531
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': 型別包含 'auto' 的符號必須具有初始設定式  
  
 指定的變數沒有初始設定式運算式。  
  
### 更正這個錯誤  
  
1.  在宣告變數時指定初始設定式運算式，例如使用等號語法的簡單指派。  
  
## 範例  
 下列範例會產生 C3531 錯誤，因為變數 `x1`、`y1, y2, y3` 和 `z2` 未初始化。  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)
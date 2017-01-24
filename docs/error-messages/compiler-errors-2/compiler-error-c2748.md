---
title: "編譯器錯誤 C2748 | Microsoft Docs"
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
  - "C2748"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2748"
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2748
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Managed 或 WinRT 陣列建立必須有陣列大小或陣列初始設定式  
  
 Managed 或 WinRT 陣列格式錯誤。  如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C2748，並示範如何修正此問題：  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```
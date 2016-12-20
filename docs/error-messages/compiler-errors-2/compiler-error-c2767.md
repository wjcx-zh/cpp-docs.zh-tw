---
title: "編譯器錯誤 C2767 | Microsoft Docs"
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
  - "C2767"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2767"
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2767
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Managed 或 WinRT 陣列維度不相符：預期應有 N 個引數 \- 提供了 M 個  
  
 Managed 或 WinRT 陣列宣告的格式錯誤。  如需詳細資訊，請參閱[陣列](../../windows/arrays-cpp-component-extensions.md)。  
  
 下列範例會產生 C2767，並說明如何加以修正：  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```
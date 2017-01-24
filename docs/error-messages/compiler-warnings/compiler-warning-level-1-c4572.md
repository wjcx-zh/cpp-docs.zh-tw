---
title: "編譯器警告 (層級 1) C4572 | Microsoft Docs"
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
  - "C4572"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4572"
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4572
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\[ParamArray\] 屬性在 \/clr 之下已被取代，請改用 '...'  
  
 使用了指定變數引數清單的過時樣式。  為 CLR 編譯時，請使用省略語法代替 <xref:System.ParamArrayAttribute>。  如需詳細資訊，請參閱[Variable Argument Lists \(...\) \(C\+\+\/CLI\)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C4572。  
  
```  
// C4572.cpp  
// compile with: /clr /W1  
void Func([System::ParamArray] array<int> ^);   // C4572  
void Func2(... array<int> ^){}   // OK  
  
int main() {  
   Func2(1, 2, 3);  
}  
```
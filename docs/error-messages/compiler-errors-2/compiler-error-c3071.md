---
title: "編譯器錯誤 C3071 | Microsoft Docs"
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
  - "C3071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3071"
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算子 'operator' 只能套用至 ref 類別或實值類型的執行個體  
  
 CLR 運算子不能在原生型別上使用。  運算子可以在 ref 類別或 ref 結構 \(實值型別\) 上使用，但不能在原生型別上使用，例如 int 或原生型別的別名，例如 System::Int32。  無法從 c \+ \+ 程式碼以參考原生變數的方式局限這些型別，因此無法使用運算子。  
  
 如需詳細資訊，請參閱 [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3071。  
  
```  
// C3071.cpp  
// compile with: /clr  
class N {};  
ref struct R {};  
  
int main() {  
   N n;  
   %n;   // C3071  
  
   R r;  
   R ^ r2 = %r;   // OK  
}  
```
---
title: "編譯器錯誤 C3072 | Microsoft Docs"
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
  - "C3072"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3072"
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3072
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算子 'operator' 不可套用至 ref 類別的執行個體  
  
 請使用一元 '`operator` ' 運算子，將 ref 類別執行個體轉換成控制代碼型別  
  
 CLR 型別需要 CLR 運算子，而不是原生 \(或標準\) 運算子。如需詳細資訊，請參閱[Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3072。  
  
```  
// C3072.cpp  
// compile with: /clr  
ref class R {};  
  
int main() {  
   R r1;  
   R^ r2 = &r1;   // C3072  
   R^ r3 = %r1;   // OK  
}  
```
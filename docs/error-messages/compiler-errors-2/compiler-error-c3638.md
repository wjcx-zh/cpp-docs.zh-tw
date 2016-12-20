---
title: "編譯器錯誤 C3638 | Microsoft Docs"
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
  - "C3638"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3638"
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3638
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 標準的 Boxing 和 Unboxing 轉換運算子不可重新定義  
  
 編譯器為每一個 Managed 類別定義轉換運算子，以支援隱含 Boxing。  這個運算子不能重新定義。  
  
 如需詳細資訊，請參閱[隱含 Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
 下列範例會產生 C3638：  
  
```  
// C3638.cpp  
// compile with: /clr  
value struct V {  
   V(){}  
   static operator V^(V);   // C3638  
};  
  
int main() {  
   V myV;  
   V ^ pmyV = myV;   // operator supports implicit boxing  
}  
```
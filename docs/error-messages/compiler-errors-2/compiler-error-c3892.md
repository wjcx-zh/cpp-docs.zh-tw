---
title: "編譯器錯誤 C3892 | Microsoft Docs"
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
  - "C3892"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3892"
ms.assetid: 83fff42c-ea48-442f-bc2e-b33a6b99d890
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3892
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 無法對 const 變數進行指定動作  
  
 const 變數在宣告並初始化之後不能再變更。  
  
 下列範例會產生 C3892：  
  
```  
// C3892.cpp  
// compile with: /clr  
ref struct Y1 {  
   static const int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3892  
}  
```
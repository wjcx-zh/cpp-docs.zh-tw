---
title: "編譯器錯誤 C3891 | Microsoft Docs"
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
  - "C3891"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3891"
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3891
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 常值資料成員不可做為左值  
  
 [literal](../../windows/literal-cpp-component-extensions.md) 變數是常數，且其值在宣告中初始化之後不可變更。  
  
 下列範例會產生 C3891：  
  
```  
// C3891.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3891  
}  
```
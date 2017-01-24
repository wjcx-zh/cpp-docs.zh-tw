---
title: "編譯器錯誤 C2267 | Microsoft Docs"
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
  - "C2267"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2267"
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2267
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 在區塊範圍內宣告靜態函式不合法  
  
 使用 `static` 宣告區域函式。  靜態函式必定為全域範圍。  
  
 下列範例會產生 C2267：  
  
```  
// C2267.cpp  
static int func2();   // OK  
int main() {  
    static int func1();   // C2267  
}  
```
---
title: "編譯器錯誤 C2104 | Microsoft Docs"
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
  - "C2104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2104"
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在位元欄位上使用 '&' 將被忽略  
  
 您不能取得位元欄位 \(Bit Field\) 的位址。  
  
 下列範例會產生 C2104：  
  
```  
// C2104.cpp  
struct X {  
   int sb : 1;  
};  
  
int main() {  
   X x;  
   &x.sb;   // C2104   
   x.sb;   // OK  
}  
```
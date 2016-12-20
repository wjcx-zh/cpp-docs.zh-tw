---
title: "編譯器錯誤 C3890 | Microsoft Docs"
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
  - "C3890"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3890"
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3890
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : 無法取得常值資料成員的位址  
  
 在記憶體回收堆積上有常數資料成員。記憶體回收堆積上的物件可加以移除，因此取得位址並不是很有用。  
  
 下列範例會產生 C3890：  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```
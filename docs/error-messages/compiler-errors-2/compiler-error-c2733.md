---
title: "編譯器錯誤 C2733 | Microsoft Docs"
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
  - "C2733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2733"
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允許多載函式 'function' 的第二個 C 連結  
  
 有一個以上的多載函式使用 C 連結宣告。  使用 C 連結時，只有一種指定函式的型式可以是外部函式。  因為多載函式具有相同的未裝飾名稱 \(Undecorated Name\)，所以它們無法用於 C 程式。  
  
 下列範例會產生 C2733：  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```
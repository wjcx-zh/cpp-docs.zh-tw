---
title: "編譯器錯誤 C2500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2500"
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2500
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier1' : 'identifier2' 已經是直接基底類別  
  
 類別或結構在基底類別 \(Base Class\) 清單中出現一次以上。  
  
 在基底清單中提到的為直接基底。  間接基底是基底清單中其中一個類別的基底類別。  
  
 類別不能被指定為直接基底類別一次以上。  類別可以用來當做間接基底類別一次以上。  
  
 下列範例會產生 C2500：  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```
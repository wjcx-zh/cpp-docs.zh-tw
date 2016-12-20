---
title: "編譯器錯誤 C2899 | Microsoft Docs"
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
  - "C2899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2899"
ms.assetid: a8942605-5bef-4d1c-b74a-41ae25423b22
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2899
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不可以在樣板宣告外部使用 typename  
  
 [typename](../../cpp/typename.md) 關鍵字只可用在樣板定義或宣告內。  在樣板宣告中，它的用法有兩種：  
  
```  
// C2899.cpp  
// compile with: /c  
template<typename T>   
class X {};  
  
// Another way  
template<class T>   
struct XX {  
   typename T::A a;   // T::A is a type  
};  
```  
  
 下列範例會產生 C2899：  
  
```  
// C2899b.cpp  
// compile with: /c  
struct Y {  
   typedef int B;  
   typename Y::B b;   // C2899  
};  
  
```
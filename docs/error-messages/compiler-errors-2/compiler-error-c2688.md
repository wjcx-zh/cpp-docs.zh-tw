---
title: "編譯器錯誤 C2688 | Microsoft Docs"
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
  - "C2688"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2688"
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2688
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'C2::fgrv' : varargs 函式不支援傳回多個或虛擬繼承的 covariant  
  
 當函式包含變數引數時，Visual C\+\+ 不支援 Covariant 傳回型別。  
  
 若要解析這項錯誤，請將函式定義為不使用變數引數，或是使所有虛擬函式都使用相同的傳回型別。  
  
 下列範例會產生 C2688：  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```
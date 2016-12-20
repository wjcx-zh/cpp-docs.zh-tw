---
title: "編譯器錯誤 C2897 | Microsoft Docs"
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
  - "C2897"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2897"
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2897
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

destructor\/finalizer 不可為函式樣板  
  
 解構函式或完成項不能進行多載，因此不允許將解構函式宣告為樣板 \(可能會定義一組解構函式\)。  
  
 下列範例會產生 C2897：  
  
## 範例  
 下列範例會產生 C2897。  
  
```  
// C2897.cpp  
// compile with: /c  
class X {  
public:  
   template<typename T> ~X() {}   // C2897  
};  
```  
  
## 範例  
 下列範例會產生 C2897。  
  
```  
// C2897_b.cpp  
// compile with: /c /clr  
ref struct R2 {  
protected:  
   template<typename T> !R2(){}   // C2897 error  
};  
```
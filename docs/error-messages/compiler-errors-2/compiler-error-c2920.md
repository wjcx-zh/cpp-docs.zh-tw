---
title: "Compiler Error C2920 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2920"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2920"
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Compiler Error C2920
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重複定義：'class'：類別樣板或泛型已宣告為 'type'  
  
 泛型或樣板類別有多個不相等的宣告。  若要修正此錯誤，請對不同的類型使用不同的名稱，或移除類型名稱的重複定義。  
  
 下列範例會產生 C2920，並顯示如何修正此問題：  
  
```  
// C2920.cpp  
// compile with: /c  
typedef int TC1;  
template <class T>   
struct TC1 {};   // C2920  
struct TC2 {};   // OK - fix by using a different name  
```  
  
 使用泛型時，也會發生 C2920。  
  
```  
// C2920b.cpp  
// compile with: /clr /c  
typedef int GC1;  
generic <class T>   
ref struct GC1 {};   // C2920  
ref struct GC2 {};   // OK - fix by using a different name  
  
```
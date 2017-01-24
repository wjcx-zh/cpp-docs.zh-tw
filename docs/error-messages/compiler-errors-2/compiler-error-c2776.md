---
title: "編譯器錯誤 C2776 | Microsoft Docs"
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
  - "C2776"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2776"
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2776
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每個屬性只可以指定一個 'get' 方法  
  
 在 [property](../../cpp/property-cpp.md) 擴充屬性中，您只能指定一個 `get` 函式。  指定多個 `get` 函式時，就會發生這項錯誤。  
  
 下列範例會產生 C2776：  
  
```  
// C2776.cpp  
struct A {  
   __declspec(property(get=GetProp,get=GetPropToo))  
   // try the following line instead  
   // __declspec(property(get=GetProp))  
      int prop;   // C2776  
   int GetProp(void);  
   int GetPropToo(void);  
};  
```
---
title: "編譯器錯誤 C3753 | Microsoft Docs"
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
  - "C3753"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3753"
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3753
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允許泛型屬性  
  
 泛型參數清單只能出現在 Managed 類別、結構或函式上。  
  
 如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)與[property](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3753。  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```
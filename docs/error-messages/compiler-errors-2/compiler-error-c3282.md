---
title: "Compiler Error C3282 | Microsoft Docs"
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
  - "C3282"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3282"
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3282
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

泛型參數清單只能出現在 Managed 或 WinRT 類別、結構或函式上  
  
 使用泛型參數清單的方式錯誤。  如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3282，並示範如何修正此問題。  
  
```  
// C3282.cpp  
// compile with: /clr /c  
generic <typename T> int x;   // C3282  
  
ref struct GC0 {  
   generic <typename T> int x;   // C3282  
};  
  
// OK  
generic <typename T>  
ref class M {};  
```
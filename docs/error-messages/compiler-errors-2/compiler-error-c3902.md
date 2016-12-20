---
title: "編譯器錯誤 C3902 | Microsoft Docs"
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
  - "C3902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3902"
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3902
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'accessor': 最後一個參數的型別必須是 'type'  
  
 至少一組方法的最後參數型別必須與屬性型別相符。  如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)。  
  
 下列範例會產生 C3902：  
  
```  
// C3902.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String ^Name {  
      void set(int);   // C3902  
      // try the following line instead  
      // void set(String^){}  
   }  
  
   property double values[int,int] {  
      void set(int, int, float);   // C3902  
      // try the following line instead  
      // void set(int, int, double){}  
   }  
};  
```
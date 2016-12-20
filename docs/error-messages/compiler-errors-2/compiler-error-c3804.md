---
title: "編譯器錯誤 C3804 | Microsoft Docs"
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
  - "C3804"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3804"
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3804
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'property\_accessor': 屬性的存取子方法必須是全部靜態或全部非靜態  
  
 定義非一般的屬性時，存取子函式可以是靜態或非靜態，但不可同時為兩者。  
  
 如需詳細資訊，請參閱[property](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3804。  
  
```  
// C3804.cpp  
// compile with: /c /clr  
ref struct A {  
  
   property int i {  
      static int get() {}  
      void set(int i) {}  
   }   // C3804 error  
  
   // OK  
   property int j {  
      int get() { return 0; }  
      void set(int i) {}  
   }  
  
   property int k {  
      static int get() { return 0; }  
      static void set(int i) {}  
   }  
};  
```
---
title: "編譯器錯誤 C3908 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3908"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3908"
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3908
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存取層級的限制少於 'construct' 的存取層級  
  
 屬性存取子方法 \(get 或 set\) 的限制存取不得少於在屬性本身上指定的存取。事件存取子方法也是同樣情形。  
  
 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 和 [event](../../windows/event-cpp-component-extensions.md)。  
  
 下列範例會產生 C3908：  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```
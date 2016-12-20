---
title: "編譯器錯誤 C3227 | Microsoft Docs"
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
  - "C3227"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3227"
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3227
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter' : 無法用 'keyword' 來尋找泛型型別  
  
 為了要將型別具現化，必須要有適當的建構函式。  但是編譯器無法確保一定有適當的建構函式可用。  
  
 您可以使用樣板代替泛型，解決這項錯誤，也可以使用幾種方法之一，建立型別的執行個體。  
  
## 範例  
 下列範例會產生 C3227。  
  
```  
// C3227.cpp  
// compile with: /clr /c  
generic<class T> interface class ICreate {  
   static T Create();  
};  
  
generic <class T>  
where T : ICreate<T>  
ref class C {  
   void f() {  
      T t = new T;   // C3227  
  
      // OK  
      T t2 = ICreate<T>::Create();  
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );  
   }  
};  
```
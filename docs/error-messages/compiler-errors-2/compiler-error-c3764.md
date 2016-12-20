---
title: "編譯器錯誤 C3764 | Microsoft Docs"
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
  - "C3764"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3764"
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3764
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override\_function': 無法覆寫基底類別方法 'base\_class\_function'  
  
 編譯器偵測到格式錯誤的覆寫。  例如，基底類別函式並非 `virtual`。  如需詳細資訊，請參閱[override](../../windows/override-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3764。  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## 範例  
 當基底類別方法同時明確並具名地加以覆寫時，可能也會發生 C3764。  下列範例會產生 C3764。  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```
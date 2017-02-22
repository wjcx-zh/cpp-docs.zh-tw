---
title: "編譯器錯誤 C3797 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3797"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3797"
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 編譯器錯誤 C3797
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override': 事件宣告不能有覆寫規範 \(應該置於事件的加入\/移除\/引發方法上\)  
  
 您不能用另外一個 trivial 事件覆寫 trivial 事件 \(即未明確定義存取子方法的事件\)。  覆寫事件必須以存取子函式定義其行為。  
  
 如需詳細資訊，請參閱[event](../../windows/event-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3797。  
  
```  
// C3797.cpp  
// compile with: /clr /c  
delegate void MyDel();  
  
ref class Class1 {  
public:  
   virtual event MyDel ^ E;  
};  
  
ref class Class2 : public Class1 {  
public:  
   virtual event MyDel ^ E override;   // C3797  
};  
  
// OK  
ref class Class3 : public Class1 {  
public:  
   virtual event MyDel ^ E {  
      void add(MyDel ^ d) override {}  
      void remove(MyDel ^ d) override {}  
   }  
};  
```
---
title: "編譯器警告 (層級 1) C4677 | Microsoft Docs"
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
  - "C4677"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4677"
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4677
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 非私用成員的簽章含有組件私用型別 'private\_type'  
  
 具有不在組件內之公用存取範圍的型別，使用了具有不在組件內之私用存取權限的型別。  參考了公用組件型別的元件，將無法使用參考了組件私用型別的型別成員。  
  
## 範例  
 下列範例會產生 C4677：  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```
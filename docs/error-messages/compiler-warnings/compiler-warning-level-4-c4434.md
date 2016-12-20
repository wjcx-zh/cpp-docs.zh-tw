---
title: "編譯器警告 (層級 4) C4434 | Microsoft Docs"
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
  - "C4434"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4434"
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4434
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類別建構函式必須有私用存取範圍，變更為私用存取  
  
 C4434 表示編譯器變更了靜態建構函式的存取範圍。  靜態建構函式必須有私用存取範圍，因為它們本來就只是要由 Common Language Runtime 呼叫的。  如需詳細資訊，請參閱 [靜態建構函式](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors)。  
  
## 範例  
 下列範例會產生 C4434：  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```
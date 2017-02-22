---
title: "編譯器錯誤 C3625 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3625"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3625"
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3625
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'native\_type'：不可以從 Managed 或 WinRT 類型 'type' 衍生原生類型  
  
 原生類別不可繼承自 Managed 或 WinRT 類別。  如需詳細資訊，請參閱[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下列範例會產生 C3625：  
  
```  
// C3625.cpp  
// compile with: /clr /c  
ref class B {};  
class D : public B {};   // C3625 cannot inherit from a managed class  
```  
  
 下列範例會產生 C3625：  
  
```  
// C3625_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class B {};  
class D : public B {};   // C3625  cannot inherit from a managed class  
```
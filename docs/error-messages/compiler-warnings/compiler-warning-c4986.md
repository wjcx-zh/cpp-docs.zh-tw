---
title: "編譯器警告 C4986 | Microsoft Docs"
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
  - "C4986"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4986"
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4986
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'︰例外狀況規格不符合上一個宣告  
  
 當在一個宣告中而不是其他宣告有例外狀況規格時，可能會產生這項警告。  
  
 C4986 預設為關閉。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4986。  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1()  
{  
    // ...  
}  
  
```  
  
## 範例  
 下列範例程式碼會消除這則警告。  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1() throw (X*)  
{  
    // ...  
}  
  
```
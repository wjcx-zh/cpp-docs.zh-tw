---
title: "編譯器警告 (層級 3) C4265 | Microsoft Docs"
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
  - "C4265"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4265"
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4265
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 類別有虛擬函式，但解構函式不是虛擬的  
  
 若類別具有虛擬函式但同時也具有非虛擬的解構函式，當透過基底類別指標終結此類別時，則可能無法正確終結該型別物件。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4265：  
  
```  
// C4265.cpp  
// compile with: /W3 /c  
#pragma warning(default : 4265)  
class B  
{  
public:  
   virtual void vmf();  
  
   ~B();  
   // try the following line instead  
   // virtual ~B();  
};   // C4265  
  
int main()  
{  
   B b;  
}  
```
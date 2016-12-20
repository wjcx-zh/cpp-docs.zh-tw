---
title: "編譯器錯誤 C2788 | Microsoft Docs"
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
  - "C2788"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2788"
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2788
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 一個以上的 GUID 和此物件關聯  
  
 [\_\_uuidof](../../cpp/uuidof-operator.md) 運算子接受附加 GUID 的使用者定義型別，或此種使用者定義型別的物件。  當引數是一個具有多個 GUID 的物件之引數時，會出現這項錯誤。  
  
 下列範例會產生 C2788：  
  
```  
// C2788.cpp  
#include <windows.h>  
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};  
template <class T, class U> class MyClass {};  
  
typedef MyClass<A,B> MyBadClass;  
typedef MyClass<A,A> MyGoodClass;  
  
int main() {  
   __uuidof(MyBadClass);    // C2788  
   // try the following line instead  
   __uuidof(MyGoodClass);  
}  
```
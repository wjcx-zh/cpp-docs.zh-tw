---
title: "編譯器錯誤 C2787 | Microsoft Docs"
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
  - "C2787"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2787"
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2787
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 沒有和此物件相關的 GUID  
  
 [\_\_uuidof](../../cpp/uuidof-operator.md) 運算子接受附加 GUID 的使用者定義型別，或此種使用者定義型別的物件。  當引數是一個不具有 GUID 的使用者定義型別時，會出現這項錯誤。  
  
 下列範例會產生 C2787：  
  
```  
// C2787.cpp  
#include <windows.h>  
struct F {};  
  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;  
  
int main() {  
   __uuidof(F);   // C2787  
   __uuidof(F2);   // OK  
}  
```
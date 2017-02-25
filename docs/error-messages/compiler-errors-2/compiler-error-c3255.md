---
title: "編譯器錯誤 C3255 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3255"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3255"
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C3255
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'value type' : 無法在原生堆積上以動態方式配置這個實值型別物件  
  
 堆疊上可以建立包含 Managed 成員之實值型別的執行個體 \(請參閱[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)\)，但堆積 \(Heap\) 上不可以建立。  
  
 下列範例會產生 C3255：  
  
```  
// C3255.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   Object^ o;  
};  
  
value struct V2 {  
   int i;  
};  
  
int main() {  
   V* pv = new V;   // C3255  
   V2* pv2 = new V2;  
   V v2;  
}  
```  
  
 **Managed Extensions for C\+\+**  
  
 下列範例會產生 C3255：  
  
```  
// C3255b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   Object* o;  
};  
  
__value struct V2 {  
   int i;  
};  
  
int main() {  
   V* pv = __nogc new V;   // C3255  
   V2* pv2 = __nogc new V2;   // OK  
}  
```
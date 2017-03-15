---
title: "編譯器錯誤 C3288 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3288"
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 編譯器錯誤 C3288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 控制代碼型別的不合法取值 \(Dereference\)  
  
 編譯器偵測到控制代碼型別的不合法取值。  您可以對控制代碼型別進行取值，然後指派給參考。  如需詳細資訊，請參閱[Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3288：  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```
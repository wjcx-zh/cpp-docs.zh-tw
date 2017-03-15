---
title: "編譯器警告 (層級 1) C4965 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4965"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4965"
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 編譯器警告 (層級 1) C4965
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

整數 0 的隱含 Box，請使用 nullptr 或明確轉型  
  
 Visual C\+\+ 具備實值型別的隱含 boxing。  使用 Managed Extensions for C\+\+ 執行 null 指派而產生的指令現在變成指派至 boxed int。  
  
 如需詳細資訊，請參閱[Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4965。  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```
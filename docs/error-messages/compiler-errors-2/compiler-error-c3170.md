---
title: "編譯器錯誤 C3170 | Microsoft Docs"
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
  - "C3170"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3170"
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3170
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在專案中不可有不同的模組識別項  
  
 在編譯的兩個檔案中發現名稱不同的 [module](../../windows/module-cpp.md) 屬性。  每一次編譯只能指定一個唯一 `module` 屬性。  
  
 可以在一個以上原始程式檔中指定完全相同的 `module` 屬性。  
  
 例如，如果找到下列 module 屬性：  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 編譯器會產生 C3170 \(請注意不同的名稱\)。
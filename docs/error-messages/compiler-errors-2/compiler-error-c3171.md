---
title: "編譯器錯誤 C3171 | Microsoft Docs"
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
  - "C3171"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3171"
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3171
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'module' : 不可以在專案中指定不同的模組屬性  
  
 編譯的兩個檔案中找到具有不同參數清單的 [module](../../windows/module-cpp.md) 屬性。  每一次編譯只能指定一個唯一 `module` 屬性。  
  
 可以在一個以上原始程式檔中指定完全相同的 `module` 屬性。  
  
 例如，如果找到下列 `module` 屬性：  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 編譯器會產生 C3171 \(請注意不同的版本值\)。
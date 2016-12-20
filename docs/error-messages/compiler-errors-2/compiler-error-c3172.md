---
title: "編譯器錯誤 C3172 | Microsoft Docs"
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
  - "C3172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3172"
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'module\_name' : 不可以在專案中指定不同的 idl\_module 屬性  
  
 在編譯的兩個檔案中找到具有相同名稱但 `dllname` 或 `version`參數不同的 [idl\_module](../../windows/idl-module.md) 屬性。  每一次編譯只能指定一個唯一 `idl_module` 屬性。  
  
 可以在一個以上原始程式檔中指定完全相同的 `idl_module` 屬性。  
  
 例如，如果找到下列 `idl_module` 屬性：  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 然後，  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 編譯器會產生 C3172 \(請注意不同的版本值\)。
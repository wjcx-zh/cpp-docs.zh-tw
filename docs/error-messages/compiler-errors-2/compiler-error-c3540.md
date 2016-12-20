---
title: "編譯器錯誤 C3540 | Microsoft Docs"
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
  - "C3540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3540"
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': sizeof 無法套用至包含 'auto' 的型別  
  
 [sizeof](../../cpp/sizeof-operator.md) 運算子無法套用至指定的型別，因為它包含 `auto` 規範。  
  
## 範例  
 下列範例會產生 C3540 錯誤。  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(推算變數類型\)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 運算子](../../cpp/sizeof-operator.md)
---
title: "編譯器錯誤 C3541 | Microsoft Docs"
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
  - "C3541"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3541"
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3541
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': typeid 無法套用至包含 'auto' 的型別  
  
 [typeid](../../windows/typeid-cpp-component-extensions.md) 運算子無法套用至指定的型別，因為它包含 `auto` 規範。  
  
## 範例  
 下列範例會產生 C3541 錯誤。  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [\/Zc:auto \(推算變數類型\)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../../windows/typeid-cpp-component-extensions.md)
---
title: "Compiler Error C3498 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3498"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3498"
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Compiler Error C3498
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var'：您無法擷取有 managed 或 WinRT 類型的變數  
  
 您無法擷取在 lambda 中有 managed 類型或 Windows 執行階段類型的變數。  
  
### 更正這個錯誤  
  
-   將 managed 或 Windows 執行階段變數傳遞至 lambda 運算式的參數清單。  
  
## 範例  
 下列範例會產生 C3498，因為具有 managed 類型的變數會出現在 lambda 運算式的擷取清單中：  
  
```  
// C3498a.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [&s](String ^ r)   
      { return String::Concat(s, r); } (", World!"); // C3498  
}  
```  
  
## 範例  
 下列範例會藉由將傳遞 managed 變數 `s` 至 lambda 運算式的擷取清單中，以解析 C3498：  
  
```  
// C3498b.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String ^ s = "Hello";  
   [](String ^ s, String ^ r)   
      { return String::Concat(s, r); } (s, ", World!");  
}  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
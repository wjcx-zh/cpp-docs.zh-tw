---
title: "編譯器錯誤 C3495 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3495"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3495"
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3495
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': Lambda 擷取必須有自動儲存期  
  
 您無法擷取沒有自動儲存期的變數，例如標記為 `static` 或 `extern` 的變數。  
  
### 更正這個錯誤  
  
-   請勿將 `static` 或 `extern` 變數傳遞至 Lambda 運算式的擷取清單。  
  
## 範例  
 下列範例會產生 C3495，因為 `static` 變數 `n` 出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3495.cpp int main() { static int n = 66; [&n]() { return n; }(); // C3495 }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)   
 [\(NOTINBUILD\)儲存類別規範](http://msdn.microsoft.com/zh-tw/10b3d22d-cb40-450b-994b-08cf9a211b6c)
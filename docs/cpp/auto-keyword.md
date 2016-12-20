---
title: "auto 關鍵字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "auto"
  - "auto_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto 關鍵字"
  - "自動儲存類別, auto 關鍵字"
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto 關鍵字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`auto` 關鍵字是一個宣告指定名稱。  不過，C\+\+ 標準為此關鍵字定義了原始和修訂的意義。  在 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 以前，`auto` 關鍵字會在「*自動*」\(Automatic\) 儲存類別中宣告變數，也就是具有區域存留期的變數。  從 [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] 開始，`auto` 關鍵字則會宣告從其宣告的初始化運算式推算類型的變數。  [\/Zc:auto&#91;\-&#93;](../build/reference/zc-auto-deduce-variable-type.md) 編譯器選項可控制 `auto` 關鍵字的意義。  
  
## 語法  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## 備註  
 `auto` 關鍵字的定義在 C\+\+ 程式語言中已經改變，但是，在 C 程式設計語言中則未改變。  
  
 下列主題描述 `auto` 關鍵字和對應的編譯器選項：  
  
-   [auto](../cpp/auto-cpp.md) 描述 `auto` 關鍵字的新定義。  
  
-   [\(NOTINBUILD\)auto Keyword \(Storage\-Class Specifier\)](http://msdn.microsoft.com/zh-tw/c7d0cecf-393d-4058-a6e6-b39e31d9edb0) 描述 `auto` 關鍵字的原始定義。  
  
-   [\/Zc:auto \(推算變數類型\)](../build/reference/zc-auto-deduce-variable-type.md) 描述告知編譯器要使用哪個 `auto` 關鍵字之定義的編譯器選項。  
  
## 請參閱  
 [\(NOTINBUILD\)Storage\-Class Specifiers](http://msdn.microsoft.com/zh-tw/10b3d22d-cb40-450b-994b-08cf9a211b6c)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)
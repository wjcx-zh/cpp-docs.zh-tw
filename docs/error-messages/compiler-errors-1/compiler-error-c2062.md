---
title: "編譯器錯誤 C2062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2062"
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的型別 'type'  
  
 編譯器 \(Compiler\) 未預期一個型別名稱。  
  
 下列範例會產生 C2062：  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 C2062 也可能會由於編譯器處理建構函式的參數清單中未定義型別的方式而發生。  如果編譯器遭遇未定義 \(拼字錯誤?\) 型別，會假設建構函式是運算式，而發出 C2062。  若要解決此問題，請使用建構函式參數清單中已定義的型別。
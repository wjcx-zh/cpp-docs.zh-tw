---
title: "編譯器錯誤 C2272 | Microsoft Docs"
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
  - "C2272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2272"
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 不允許在靜態成員函式上使用修飾詞 \(Modifier\)  
  
 使用記憶體模型規範，宣告了 `static` 成員函式，例如 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md)，而這類修飾詞不允許用於 `static` 成員函式上。  
  
 下列範例會產生 C2272：  
  
```  
// C2272.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1() const volatile;   // C2272  func1 is static  
   void func2() const volatile;   // OK  
};  
```
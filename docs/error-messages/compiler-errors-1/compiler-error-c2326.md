---
title: "編譯器錯誤 C2326 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2326"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2326"
ms.assetid: 01a5ea40-de83-4e6f-a4e8-469f441258e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2326
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declarator': 函式無法存取 'name'  
  
 這個程式碼嘗試修改成員變數，這是不可執行的作業。  
  
## 範例  
 下列範例會產生 C2326：  
  
```  
// C2326.cpp void MyFunc() { int i; class MyClass  { public: void mf() { i = 4;   // C2326 i is inaccessible } }; }  
```
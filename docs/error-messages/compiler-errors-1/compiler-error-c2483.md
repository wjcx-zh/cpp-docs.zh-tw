---
title: "編譯器錯誤 C2483 | Microsoft Docs"
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
  - "C2483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2483"
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 具有建構函式或解構函式的物件不可宣告為 'thread'  
  
 以 `thread` 屬性宣告的變數不能使用需要執行階段評估的建構函式或其他運算式加以初始化。  需要有靜態運算式，才能初始化 `thread` 資料。  
  
## 範例  
 下列範例會產生 C2483。  
  
```  
// C2483.cpp  
// compile with: /c  
__declspec(thread) struct A {  
   A(){}  
   ~A(){}  
} aa;   // C2483 error  
  
__declspec(thread) struct B {} b;   // OK  
```  
  
## 請參閱  
 [執行緒](../../cpp/thread.md)
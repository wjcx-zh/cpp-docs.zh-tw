---
title: "編譯器警告 (層級 4) C4268 | Microsoft Docs"
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
  - "C4268"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4268"
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4268
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 使用編譯器產生的預設建構函式初始化宣告為 'const' 的靜態\/全域資料，物件的值皆為零  
  
 非 Trivial 類別的 **const** 全域或靜態執行個體由編譯器產生的預設建構函式進行初始化。  
  
## 範例  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 由於這個類別執行個體為 **const**，`m_data` 的值無法更改。
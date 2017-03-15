---
title: "編譯器錯誤 C2348 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2348"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2348"
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2348
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type name' : 不是 C\-Style 彙總，無法在內嵌 IDL 中匯出  
  
 若要將 `struct` 放在具有 [export](../../windows/export.md) 屬性的 .idl 檔內，`struct` 必須只包含資料。  
  
 下列範例會產生 C2348：  
  
```  
// C2348.cpp  
// C2348 error expected  
[ module(name="SimpleMidlTest") ];  
  
[export]  
struct Point {  
   // Delete the following two lines to resolve.  
   Point() : m_i(0), m_j(0) {}  
   Point(int i, int j) : m_i(i), m_j(j) {}  
  
   int m_i;  
   int m_j;  
};  
```
---
title: "運算陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算陳述式"
  - "陳述式, 運算式"
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

運算陳述式會造成對於運算式的評估。  運算陳述式不會發生控制權轉移或反覆項目的情形。  
  
 運算陳述式的語法很簡單  
  
## 語法  
  
```  
[expression ] ;  
```  
  
## 備註  
 在下一個陳述式執行之前，會完成運算陳述式中所有運算式的評估，以及所有副作用。  最常見的運算陳述式是指派和函式呼叫。由於運算式是選擇性的，單獨的分號會視為是空的運算陳述式，稱為 [null](../cpp/null-statement.md) 陳述式。  
  
## 請參閱  
 [C\+\+ 陳述式概觀](../cpp/overview-of-cpp-statements.md)
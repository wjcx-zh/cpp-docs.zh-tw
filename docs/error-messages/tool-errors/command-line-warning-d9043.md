---
title: "命令列警告 D9043 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9043"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9043"
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令列警告 D9043
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無效的值 'warning\_level' \(對 'compiler\_option' 而言\)，假設為 '4999'。程式碼分析警告未與警告層級關聯  
  
## 範例  
 下列範例會產生 C9043。  
  
```  
// D9043.cpp  
// compile with: /analyze /w16001  
// D9043 warning expected  
int main() {}  
```
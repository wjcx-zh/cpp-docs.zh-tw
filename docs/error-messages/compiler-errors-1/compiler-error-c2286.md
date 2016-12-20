---
title: "編譯器錯誤 C2286 | Microsoft Docs"
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
  - "C2286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2286"
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' 表示的成員指標已經設定為 'inheritance' \- 已忽略宣告  
  
 類別有兩種 pointer\-to\-member 表示。  
  
 如需詳細資訊，請參閱[繼承關鍵字](../../cpp/inheritance-keywords.md)。  
  
## 範例  
 下列範例會產生 C2286：  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```
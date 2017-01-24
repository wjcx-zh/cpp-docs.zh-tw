---
title: "編譯器警告 (層級 1) C4138 | Microsoft Docs"
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
  - "C4138"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4138"
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4138
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在註解外部找到 '\*\/'  
  
 結案註解分隔符號必須在開啟註解分隔符號之後。 編譯器會假設星號 \(**\***\) 和正斜線 \(\/\) 之間有個空格。  
  
## 範例  
  
```  
// C4138a.cpp // compile with: /W1 int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning int main() { }  
```  
  
 此警告可能因嘗試巢狀化註解所致。  
  
 如果您將包含註解的程式碼區段註解化，再將程式碼括在 **\#if \/ \#endif** 區塊中，並將控制運算式設定為零，應可解決此警告：  
  
```  
// C4138b.cpp // compile with: /W1 #if 0 int my_variable;   /* Declaration currently not needed */ #endif int main() { }  
```
---
title: "程式終止中的 return 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料類型 [C++], 函式傳回類型"
  - "函式傳回類型, return 陳述式"
  - "return 關鍵字 [C++], 語法"
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 程式終止中的 return 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 **main** 發出 `return` 陳述式在功能上相當於呼叫 **exit** 函式。  參考下列範例：  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 上述範例中的 **exit** 和 `return` 陳述式的功能相同。  不過，C\+\+ 要求使用具有傳回類型 \(非 `void`\) 的函式傳回一個值。  `return` 陳述式可讓您從 **main** 傳回值。  
  
## 請參閱  
 [程式終止](../cpp/program-termination.md)
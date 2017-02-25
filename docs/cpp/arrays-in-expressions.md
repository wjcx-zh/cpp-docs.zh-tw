---
title: "運算式中的陣列 | Microsoft Docs"
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
  - "陣列 [C++], 在運算式中"
  - "運算式 [C++], 其中的陣列"
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 運算式中的陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當陣列類型的識別項出現在 `sizeof`、傳址 \(**&**\)，或是參考的初始化中時，會將它轉換成第一個陣列元素的指標。  例如：  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 指標 `psz` 會指向陣列 `szError1` 的第一個元素。  請注意，陣列 \(和指標不同\) 不是可修改的左值。  因此，下列指派是不合法的：  
  
```  
szError1 = psz;  
```  
  
## 請參閱  
 [陣列](../cpp/arrays-cpp.md)
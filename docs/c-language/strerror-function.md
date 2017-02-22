---
title: "strerror 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strerror 函式"
ms.assetid: 9fb9366e-d9a8-47d4-ad51-d98774a0617f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# strerror 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.11.6.2** `strerror` 函式傳回的錯誤訊息字串內容  
  
 `strerror` 函式會產生下列訊息：  
  
```  
0   Error 0  
1    
2   No such file or directory  
3    
4    
5    
6    
7   Arg list too long  
8   Exec format error  
9   Bad file number  
10    
11    
12  Not enough core  
13  Permission denied  
14    
15    
16    
17  File exists  
18  Cross-device link  
19    
20    
21    
22  Invalid argument  
23    
24  Too many open files  
25    
26    
27    
28  No space left on device  
29    
30    
31    
32    
33  Math argument  
34  Result too large  
35    
36  Resource deadlock would occur  
```  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)
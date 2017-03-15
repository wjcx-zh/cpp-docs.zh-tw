---
title: "保留字 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "code"
  - "CONFORMING"
  - "DISCARDABLE"
  - "Description"
  - "base"
  - "APPLOADER"
  - "Data"
  - "DYNAMIC"
  - "DEV386"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def 檔案 [C++], 保留字"
  - "def 檔案 [C++], 保留字"
  - "連結器 [C++], 保留字"
  - "保留字 [C++]"
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 保留字
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以下是連結器的保留字。  只有當名稱是以雙引號 \(""\) 括住時，才能在[模組定義陳述式](../../build/reference/module-definition-dot-def-files.md)中使用這些名稱做為引數。  
  
||||  
|-|-|-|  
|**APPLOADER**1|**INITINSTANCE**2|**PRELOAD**|  
|**BASE**|**IOPL**|**PRIVATE**|  
|**CODE**|**LIBRARY**1|**PROTMODE**2|  
|**CONFORMING**|**LOADONCALL**1|**PURE**1|  
|**DATA**|**LONGNAMES**2|**READONLY**|  
|**DESCRIPTION**|`MOVABLE`1|**READWRITE**|  
|**DEV386**|**MOVEABLE**1|**REALMODE**1|  
|**DISCARDABLE**|**MULTIPLE**|**RESIDENT**|  
|**DYNAMIC**|**NAME**|**RESIDENTNAME**1|  
|**EXECUTE\-ONLY**|**NEWFILES**2|**SECTIONS**|  
|**EXECUTEONLY**|`NODATA`1|**SEGMENTS**|  
|**EXECUTEREAD**|**NOIOPL**1|**SHARED**|  
|**EXETYPE**|**NONAME**|**SINGLE**|  
|**EXPORTS**|**NONCONFORMING**1|**STACKSIZE**|  
|**FIXED**1|**NONDISCARDABLE**|**STUB**|  
|**FUNCTIONS**2|**NONE**|**VERSION**|  
|**HEAPSIZE**|**NONSHARED**|**WINDOWAPI**|  
|**IMPORTS**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**IMPURE**1|**OBJECTS**|**WINDOWS**|  
|**INCLUDE**2|**OLD**1||  
  
 1 連結器在碰到這個字的時候會發出警告 \(「已忽略」\)。  不過，這個字仍然會被保留。  
  
 2 連結器會忽略這個字，但是不會發出警告。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)
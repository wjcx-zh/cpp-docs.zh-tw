---
title: "編譯器警告 (層級 1) C4632 | Microsoft Docs"
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
  - "C4632"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4632"
ms.assetid: 9e35d205-cf21-4e34-8bd5-e1e7b0e2cdd3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4632
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文件註解：檔案 \- 存取遭拒：原因  
  
 至 .xdc 檔 \(`file`\) 的路徑無效，而且並未建立 .xdc 檔。  
  
 下列範例會產生 C4632：  
  
```  
// C4632.cpp  
// compile with: /clr /docv:\\falsedir /LD /W1  
// C4632 expected  
  
/// Text for class MyClass.  
public ref class MyClass {};  
```
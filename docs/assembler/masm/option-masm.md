---
title: "OPTION (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "option"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OPTION directive"
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# OPTION (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用和停用的組譯工具的功能。  
  
## 語法  
  
```  
  
OPTION   
optionlist  
  
```  
  
## 備註  
 可用的選項包括：  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模擬器**|  
|**NOEMULATOR**|**終**|**EXPR16**|**EXPR32**|  
|**語言**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**位移**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**程序**|**初構**|**READONLY**|**NOREADONLY**|  
|**範圍**|**NOSCOPED**|**區段**|**SETIF2**。|  
  
 語言的語法是**選項語言：***x*，其中  *x* C、 系統呼叫、 服務繼續操作，依照 pascal 命名法、 FORTRAN 或基本的。  系統呼叫、 pascal 命名法、 FORTRAN 和 BASIC 不支援搭配[.MODEL](../../assembler/masm/dot-model.md)平面。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)
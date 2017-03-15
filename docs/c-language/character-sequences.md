---
title: "字元順序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字元順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.8.2**：原始程式檔字元序列的對應  
  
 除了不支援逸出序列以外，前置處理器陳述式使用的字元集與原始程式檔陳述式使用的相同。  
  
 因此，若要指定 Include 檔案的路徑，則只需要使用一個反斜線：  
  
```  
#include "path1\path2\myfile"  
```  
  
 在原始程式碼內必須使用兩個反斜線：  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## 請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)
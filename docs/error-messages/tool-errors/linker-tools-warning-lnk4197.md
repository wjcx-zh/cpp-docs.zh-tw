---
title: "連結器工具警告 LNK4197 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4197"
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 連結器工具警告 LNK4197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匯出指定多次的 'exportname'；使用第一次的指定  
  
 匯出的指定次數超過一次且每次都不同。  連結器將使用第一次的指定，並忽略其他指定內容。  
  
 如果您是要重建 C 執行階段程式庫，請忽略這個訊息。  
  
 如果以相同方式多次指定匯出，連結器就不會發出警告。  
  
 例如，下列 .def 檔的內容會造成這個警告：  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### 若要修正，請檢查下列可能原因  
  
1.  命令列 \(透過 export:\) 和 .def 檔中指定了同一個匯出。  
  
2.  .def 檔以不同屬性列出兩次相同的匯出。
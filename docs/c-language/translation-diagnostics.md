---
title: "轉譯：診斷 | Microsoft Docs"
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
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 轉譯：診斷
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 2.1.1.3**：如何識別診斷  
  
 Microsoft C 會產生下列格式的錯誤訊息：  
  
```  
  
filename( line-number ) : diagnostic Cnumber message  
```  
  
 其中 *filename* 是發生錯誤所在的原始程式檔名稱，*line\-number* 是編譯器偵測到錯誤的行號，`diagnostic` 是「錯誤」或「警告」，`number` 是用於識別錯誤或警告的唯一四位數字 \(前面加上 **C**，如語法中所註解\)，而 `message` 是說明訊息。  
  
## 請參閱  
 [實作定義的行為](../c-language/implementation-defined-behavior.md)
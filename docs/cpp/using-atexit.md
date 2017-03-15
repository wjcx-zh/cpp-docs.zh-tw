---
title: "使用 atexit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atexit 函式"
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用 atexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 [atexit](../c-runtime-library/reference/atexit.md) 函式指定在程式結束之前執行的結束處理函式。  執行結束處理函式之前，不會終結在呼叫 `atexit` 之前初始化的全域靜態物件。  
  
## 請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)
---
title: "配置零記憶體 | Microsoft Docs"
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
helpviewer_keywords: 
  - "記憶體配置, 零記憶體"
  - "零記憶體"
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 配置零記憶體
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.10.3**：`calloc`、`malloc` 或 `realloc` 函式在所要求的大小為零時的行為  
  
 `calloc`、`malloc` 和 `realloc` 函式接受零做為引數。  其中未實際配置記憶體，不過會傳回有效的指標，而且稍後可以藉由 realloc 修改記憶體區塊。  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)
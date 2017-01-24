---
title: "推斷規則的優先順序 | Microsoft Docs"
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
helpviewer_keywords: 
  - "NMAKE 中的推斷規則"
  - "優先順序, 推斷規則"
  - "規則, 推斷"
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推斷規則的優先順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果介面規則有多重定義，NMAKE 會使用最高優先權的定義。  下列清單從最高到最低，顯示出優先順序：  
  
1.  在 Makefile 中定義的介面規則，較新的定義具有優先權。  
  
2.  在 Tools.ini 中定義的介面規則，較新的定義具有優先權。  
  
3.  預先定義的介面規則。  
  
## 請參閱  
 [推斷規則](../build/inference-rules.md)
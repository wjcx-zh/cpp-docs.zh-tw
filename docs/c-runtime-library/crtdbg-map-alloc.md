---
title: "_CRTDBG_MAP_ALLOC | Microsoft Docs"
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
  - "CRTDBG_MAP_ALLOC"
  - "_CRTDBG_MAP_ALLOC"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC 巨集"
  - "記憶體配置，在偵錯組建中"
  - "CRTDBG_MAP_ALLOC 巨集"
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CRTDBG_MAP_ALLOC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當 **\_CRTDBG\_MAP\_ALLOC** 旗標在應用程式的偵錯版本中定義，堆積函式的基底版本直接對應到它們的偵錯版本。  旗標可用來 Crtdbg.h 進行對應。  在應用程式時表示 [\_DEBUG](../c-runtime-library/debug.md) 旗標，定義這個旗標才可以使用。  
  
 如需使用偵錯版本的詳細資訊給堆積函式的基底版本，請參閱 [使用偵錯版本與基底版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 請參閱  
 [控制旗標](../c-runtime-library/control-flags.md)
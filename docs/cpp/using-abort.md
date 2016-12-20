---
title: "使用 abort | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort 函式"
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 abort
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呼叫 [abort](../c-runtime-library/reference/abort.md) 函式會導致立即終止。  它會略過初始化全域靜態物件的正常解構流程。  另外也會略過任何使用 `atexit` 函式指定的特殊處理。  
  
## 請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)
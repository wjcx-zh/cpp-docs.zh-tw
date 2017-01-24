---
title: "陣列大小上限 | Microsoft Docs"
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
ms.assetid: 4c782cf6-73f3-40b0-b306-229d22da4ee1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 陣列大小上限
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.3.3.4, 4.1.1** 需要保留陣列大小最大值的整數型別 \(即為 **size\_t** 的大小\)。  
  
 `size_t` typedef 是在 32 位元 x86 平台的 `unsigned int` 。  在 64 位元平台上， `size_t` typedef 為 **unsigned \_\_int64**。  
  
## 請參閱  
 [陣列和指標](../c-language/arrays-and-pointers.md)
---
title: "資源編譯器嚴重錯誤 RC1018 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1018"
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器嚴重錯誤 RC1018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的 '\#elif'  
  
 `#elif` 指示詞並沒有出現在 `#if`、**\#ifdef** 或 **\#ifndef** 建構 \(Construct\) 中。  
  
 請確定在這個陳述式之前有指定的 `#if`、**\#ifdef** 或 **\#ifndef** 陳述式。
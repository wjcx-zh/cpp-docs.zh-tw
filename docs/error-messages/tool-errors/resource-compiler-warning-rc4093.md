---
title: "資源編譯器警告 RC4093 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC4093"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4093"
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器警告 RC4093
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非作用中的程式碼字元常數中包含新行字元  
  
 `#if`、`#elif`、**\#ifdef** 或 **\#ifndef** 前置處理器指示詞 \(Preprocessor Directive\) 的常數運算式評估為零，使得之後的程式碼停止使用。  在停止使用之程式碼中，單引號或雙引號中出現新行字元。  
  
 在下一個雙引號出現之前，所有文字都視為字元常數的一部分。
---
title: "編譯器警告 (層級 1) C4276 | Microsoft Docs"
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
  - "C4276"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4276"
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4276
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 未提供原型; 假設沒有參數  
  
 當您用 [\_\_stdcall](../../cpp/stdcall.md) 呼叫慣例取得函式的位址時，必須提供原型，編譯器才能建立該函式的裝飾名稱。  由於 *function* 沒有原型，編譯器在建立裝飾名稱時會假設該函式沒有參數。
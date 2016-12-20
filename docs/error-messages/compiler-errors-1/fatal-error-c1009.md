---
title: "嚴重錯誤 C1009 | Microsoft Docs"
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
  - "C1009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1009"
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：巨集巢狀結構太深  
  
 編譯器嘗試同時展開的巨集太多。  編譯器在巢狀巨集有 256 層的限制。  請將巢狀巨集分割成較簡單的巨集。
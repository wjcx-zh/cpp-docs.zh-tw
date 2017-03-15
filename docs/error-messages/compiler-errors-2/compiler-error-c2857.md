---
title: "編譯器錯誤 C2857 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2857"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2857"
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2857
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在原始程式檔中找不到以 \/Ycfilename 命令列選項指定的 '\#include' 陳述式  
  
 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 選項指定了沒有包含在編譯的原始程式檔 \(Source File\) 中的包含檔檔名。  
  
 這項錯誤可能是因條件式編譯區塊中未經過編譯的 `#include` 陳述式而造成。
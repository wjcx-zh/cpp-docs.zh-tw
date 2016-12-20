---
title: "編譯器警告 (層級 2) C4653 | Microsoft Docs"
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
  - "C4653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4653"
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器選項 'option' 與先行編譯標頭檔不相容；忽略目前的命令列選項  
  
 和使用先行編譯標頭檔 \([\/Yu](../../build/reference/yu-use-precompiled-header-file.md)\) 選項一起指定的選項與建立先行編譯標頭時指定的選項不一致。  此次編譯會使用建立先行編譯標頭時指定的選項。  
  
 在編譯先行編譯標頭時為 Pack Structures 選項 \([\/Zp](../../build/reference/zp-struct-member-alignment.md)\) 指定不同的值，就會發生此警告。
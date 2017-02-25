---
title: "嚴重錯誤 C1005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1005"
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 嚴重錯誤 C1005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串太大超過緩衝區  
  
 編譯器中繼檔案中的字串造成緩衝區溢位。  
  
 當您傳遞至 [\/Fd](../../build/reference/fd-program-database-file-name.md) 或 [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 編譯器選項的參數大於 256 個位元組時，可能會取得這項錯誤。
---
title: "回溯相容性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回溯相容性"
  - "回溯相容性, C 執行階段程式庫"
  - "相容性, C 執行階段程式庫"
  - "CRT, 相容性"
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 回溯相容性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於產品版本之間的相容性，程式庫 OLDNAMES.LIB 對應舊名稱的新名稱。  例如， `_open`的 `open` 對應。  只有在您編譯命令列選項的下列組合時，您必須使用 OLDNAMES.LIB 明確連結:  
  
-   `/Zl` \(省略預設程式庫名稱從目的檔\) 和 `/Ze` \(預設值—使用 Microsoft 擴充功能\)  
  
-   `/link` \(連結器控制項\)，則為 `/NOD` \(沒有預設程式庫搜尋\) 和 `/Ze`  
  
 如需編譯器命令列選項的詳細資訊，請參閱 [編譯器參考](../build/reference/compiler-options.md)。  
  
## 請參閱  
 [相容性](../c-runtime-library/compatibility.md)
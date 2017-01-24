---
title: "輸入和輸出 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "I/O [CRT]"
  - "I/O [CRT], 常式"
  - "I/O 常式"
  - "輸入常式"
  - "輸出常式"
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入和輸出
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I\/O 函式來回檔案和裝置讀取和寫入資料。  檔案 I\/O 作業在文字模式或二進位模式下發生。  Microsoft Run\-Time 程式庫有三種類型的 I\/O 函式有：  
  
-   [資料流 I\/O](../c-runtime-library/stream-i-o.md) 函式會將資料當做個別字元資料流。  
  
-   [低階 I\/O](../c-runtime-library/low-level-i-o.md) 函式比資料流 I\/O 所提供之叫用作業系統直接低階作業的。  
  
-   [主控台和連接埠 I\/O](../c-runtime-library/console-and-port-i-o.md) 函式會直接寫入主控台 \(鍵盤和螢幕\) 或 I\/O 埠讀取或寫入 \(例如印表機通訊埠\)。  
  
    > [!NOTE]
    >  由於目前函式在緩衝區而低階函式不是，函式的這兩種型別通常不相容。  用於管理特定檔案，請使用完整的資料流或低階函式。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
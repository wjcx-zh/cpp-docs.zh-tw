---
title: "嚴重錯誤 C1081 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1081"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1081"
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 嚴重錯誤 C1081
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': 檔名太長  
  
 檔案路徑名稱長度超過 `_MAX_PATH` \(STDLIB.h 定義為 260 個字元\)，  請縮短檔案名稱。  
  
 如果您以短檔名來呼叫 CL.exe，編譯器可能需要產生一個完整的路徑名稱。  例如，`cl -c myfile.cpp` 可能會使編譯器產生：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```
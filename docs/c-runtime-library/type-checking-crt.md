---
title: "類型檢查 (CRT) | Microsoft Docs"
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
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "檢查類型"
  - "類型檢查"
  - "變數引數函式"
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 類型檢查 (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

行條件類型如下檢查可接受引數的變數數字的函式的編譯器：  
  
|函式呼叫|型別檢查引數|  
|----------|------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|第一個引數 \(格式字串\)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|前兩個引數 \(檔案或緩衝區和格式字串\)|  
|`_snprintf_s`|前三個引數 \(檔案或緩衝區、計數和格式字串\)|  
|`_open`|前兩個引數 \(路徑和 `_open` 旗標\)|  
|`_sopen_s`|前三個引數 \(路徑， `_open` 旗標和共用模式\)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|前兩個引數 \(路徑和第一個引數指標\)|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|前三個引數 \(模式旗標、路徑和第一個引數指標\)|  
  
 執行相同的限制型別檢查這些函式寬字元對應的編譯器。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
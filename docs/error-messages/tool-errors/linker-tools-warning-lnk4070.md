---
title: "連結器工具警告 LNK4070 | Microsoft Docs"
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
  - "LNK4070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4070"
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/OUT:filename 指示詞於 .EXP 與輸出檔名 'filename' 不同；忽略指示詞  
  
 建立 .exp 檔時，在 [NAME](../../build/reference/name-c-cpp.md) 或 [LIBRARY](../../build/reference/library.md) 陳述式中指定的 `filename` 不同於預設或以 [\/OUT](../../build/reference/out-output-file-name.md) 選項指定的輸出檔 `filename`。  
  
 如果您變更開發環境中的輸出檔名稱，且開發環境中專案的 .def 檔未曾更新，您便會看到這個警告。  請手動更新 .def 檔以解決這個警告。  
  
 使用這個 DLL 的用戶端程式可能會發生問題。
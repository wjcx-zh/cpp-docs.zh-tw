---
title: "連結器工具錯誤 LNK2023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2023"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2023"
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK2023
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

錯誤的 dll 或進入點 \<dll 或進入點\>  
  
 連結器載入錯誤版本的 msobj90.dll。  請確認路徑中的 link.exe 和 msobj90.dll 的版本相同。  
  
 可能沒有 msobj90.dll 的相依項。  msobj90.dll 相依項清單為：  
  
-   Msvcr90.dll  
  
-   Kernel32.dll  
  
 請檢查您的電腦中是否有任何其他 msobj90.dll 可能已過期的複本。
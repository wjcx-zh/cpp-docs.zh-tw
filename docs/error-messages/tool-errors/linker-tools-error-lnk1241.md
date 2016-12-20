---
title: "連結器工具錯誤 LNK1241 | Microsoft Docs"
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
  - "LNK1241"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1241"
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1241
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已指定資源檔 'resource file'  
  
 如果您在命令列手動執行 **cvtres**，接著又將所產生的 .obj 檔連同其他 .res 檔傳遞至連結器，就會發生這種錯誤。  
  
 若要指定多個 .res 檔，請將它們全部以 .res 檔傳遞至連結器，而不要從 **cvtres** 建立的 .obj 檔之內傳遞。
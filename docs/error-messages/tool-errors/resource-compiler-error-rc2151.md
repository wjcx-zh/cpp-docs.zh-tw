---
title: "資源編譯器錯誤 RC2151 | Microsoft Docs"
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
  - "RC2151"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2151"
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器錯誤 RC2151
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法重複使用字串常數  
  
 您在 **STRINGTABLE** 陳述式中使用兩次相同的值，  請確定您未混淆重疊的十進位及十六進位值。  
  
 **STRINGTABLE** 中的每項 ID 都必須具有唯一性。  為了達到最高的效率，請使用 16 倍數開始的連續常數。
---
title: "運算錯誤 M6205 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6205"
ms.assetid: fd28e7c9-a463-4a9c-a863-cc9e75315550
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算錯誤 M6205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': \_TLOSS 錯誤  
  
 發生合計數字精確度 \(precision\) 喪失。  
  
 此錯誤可能是因為給定非常大的值做為 sin、cos 或 tan 的運算元所造成，因為運算元必須減少為 0 到 2\*pi 間的數字。
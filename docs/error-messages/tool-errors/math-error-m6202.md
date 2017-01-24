---
title: "運算錯誤 M6202 | Microsoft Docs"
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
  - "M6202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6202"
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算錯誤 M6202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': \_SING 錯誤  
  
 給定函式的引數為函式異常值。  函式並未定義該引數。  
  
 這項錯誤會以函式名稱、函式的引數和錯誤類型來呼叫 `_matherr` 函式。  您可以重新撰寫 `_matherr` 函式來自訂某些執行階段浮點運算錯誤的處理。
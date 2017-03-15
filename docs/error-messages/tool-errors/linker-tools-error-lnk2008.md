---
title: "連結器工具錯誤 LNK2008 | Microsoft Docs"
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
  - "LNK2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2008"
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修復目標不對齊 'symbol\_name'  
  
 LINK 在您的目的檔中找到未正確對齊的修復目標。  
  
 自訂區段對齊 \(例如，\#pragma [pack](../../preprocessor/pack.md)\)、[align](../../cpp/align-cpp.md) 修飾詞，或是使用修飾區段對齊的組件語言程式碼，都可能會造成這項錯誤。  
  
 如果您的程式碼不使用上述任何一項，錯誤可能是由編譯器造成。
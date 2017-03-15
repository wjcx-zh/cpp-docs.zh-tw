---
title: "嚴重錯誤 C1854 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1854"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1854"
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1854
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法覆寫在目的檔中先行編譯標頭檔建立期間形成的資訊: 'filename'  
  
 您在相同檔案指定**\/Yc** \(建立預先編譯標頭\) 選項之後，又指定**\/Yu** \(使用先行編譯標頭\) 選項。  某些宣告 \(例如包括 `__declspec` `dllexport` 的宣告\) 會使這種動作無效。
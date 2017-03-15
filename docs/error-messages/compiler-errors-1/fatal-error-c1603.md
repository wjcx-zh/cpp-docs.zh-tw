---
title: "嚴重錯誤 C1603 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1603"
ms.assetid: e5a06925-f916-4637-8240-6d2d280e6124
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1603
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

內嵌組譯碼分支目標超過範圍 number 個位元組  
  
 JCXZ 或 JECXZ 指令和其指定目標標籤 \(Label\) 之間計算出來的距離大於 128 個位元組。  請更新您的程式碼，讓此標籤更接近指令。
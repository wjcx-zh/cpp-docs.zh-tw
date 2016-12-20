---
title: "編譯器警告 (層級 1) C4420 | Microsoft Docs"
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
  - "C4420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4420"
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 無法使用運算子，使用 'operator' 代替; 執行階段檢查可能無法執行  
  
 當您使用 [\/RTCv](../../build/reference/rtc-run-time-error-checks.md) \(向量新增\/刪除檢查\) 以及當沒有向量格式時，會產生此警告。  在這種情況下會使用非向量格式。  
  
 為了要使 \/RTCv 正確運作，使用向量語法時，編譯器應該要呼叫 [new](../../cpp/new-operator-cpp.md)\/[delete](../../cpp/delete-operator-cpp.md) 向量格式。
---
title: "_crtDbgFlag | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_crtDbgFlag"
  - "crtDbgFlag"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_crtDbgFlag 常數"
  - "crtDbgFlag 常數"
  - "偵錯堆積, 控制旗標"
  - "偵錯堆積, 追蹤其上的記憶體"
  - "啟用記憶體配置追蹤旗標"
  - "記憶體配置, 追蹤旗標"
  - "記憶體, 偵錯堆積上的追蹤"
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _crtDbgFlag
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\_crtDbgFlag** 旗標包含五個位元欄位，可控制要追蹤、驗證、報告及傾印偵錯版本的堆積中的多少記憶體。  旗標的位元欄位使用 [\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函式加以設定。  此旗標及其欄位會宣告於 Crtdbg.h 中。  只有當應用程式中已定義 [\_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。  
  
 如需搭配其他偵錯函式使用此旗標的詳細資訊，請參閱[堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  
  
## 請參閱  
 [控制旗標](../c-runtime-library/control-flags.md)
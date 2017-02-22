---
title: "多執行緒程式庫效能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程式庫, 多執行緒"
  - "多執行緒程式庫"
  - "效能, 多執行緒"
  - "執行緒 [C++], 效能"
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 多執行緒程式庫效能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

單一執行緒 CRT 已無法使用。  本主題討論如何從多個執行緒的程式庫取得最高性能。  
  
## 最大化效能  
 改善了多執行緒的程式庫的效能並接近現在已排除的單一執行緒的程式庫的效能。  針對這些需要更高的效能情況下，有許多新功能。  
  
-   獨立資料流鎖定允許您鎖定資料流並使用直接存取資料流的 [\_nolock 函式](../c-runtime-library/nolock-functions.md) 。  這可讓鎖定用法在重要迴圈外提取。  
  
-   各個執行緒地區設定減少多執行緒案例中地區設定存取的成本 \(請參閱 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)\)。  
  
-   地區設定相關的函式 \(名稱結尾為 \_l\) 會將地區設定做為參數，取消大量成本 \(例如， [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\)。  
  
-   對常見的字碼頁的最佳化減少許多簡短作業的成本。  
  
-   定義 [\_CRT\_DISABLE\_PERFCRIT\_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) 強制任何 I\/O 作業假設單一執行緒的 I\/O 模型和使用函式的 \_nolock 形式。  這允許高度 I\/O 的單一執行緒應用程式取得更好的效能。  
  
-   CRT 堆積控制代碼的公開可讓您啟用 CRT 堆積的 Windows Low Fragmentation Heap \(LFH\)，可大幅改善高度縮放的情況的效能。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
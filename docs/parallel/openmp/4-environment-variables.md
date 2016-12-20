---
title: "4. Environment Variables | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4. Environment Variables
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節將告訴您，OpenMP C 和 C\+\+ API 的環境變數 \(或同等的平台特定的機制\)，以決定的平行處理程式碼執行。  環境變數的名稱必須是大寫。  指派給它們的值是不區分大小寫，而且可能會有前置和後端空白字元。  修改程式啟動後的值會被忽略。  
  
 環境變數如下所示：  
  
-   **OMP\_SCHEDULE** 設定執行階段排程類型和區塊大小。  
  
-   **OMP\_NUM\_THREADS** 設定為在執行期間所使用的執行緒數目。  
  
-   **OMP\_DYNAMIC** 啟用或停用動態調整執行緒的數目。  
  
-   **OMP\_NESTED** 啟用或停用巢狀的平行處理原則。  
  
 這一章中的範例只會示範在 Unix C 殼層 \(csh\) 的環境中設定這些變數可能方式。  在 \[Korn 殼層和 DOS 環境動作很類似，，如下所示：  
  
 csh：  
 setenv OMP\_SCHEDULE"dynamic"  
  
 ksh：  
 匯出 OMP\_SCHEDULE \= 「 動態 」  
  
 DOS：  
 設定 OMP\_SCHEDULE \= 「 動態 」
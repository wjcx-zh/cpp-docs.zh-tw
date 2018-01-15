---
title: "4. 環境變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cef1bac78afbcc8b852c3bd42e0904e1963137c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="4-environment-variables"></a>4.環境變數
本章節描述 OpenMP C 和 c + + 應用程式開發介面的環境變數 （或對等平台特定的機制），控制平行程式碼的執行。  環境變數名稱必須是大寫。 指派給它們的值不區分大小寫，而且可能會有開頭和尾端空白字元。  修改程式啟動之後的值都會被忽略。  
  
 環境變數如下所示：  
  
-   **OMP_SCHEDULE**設定執行階段排程類型和區塊大小。  
  
-   **OMP_NUM_THREADS**設定執行期間要使用的執行緒數目。  
  
-   **OMP_DYNAMIC**啟用或停用動態調整執行緒數目。  
  
-   **OMP_NESTED**啟用或停用巢狀平行處理原則。  
  
 本章節中的範例只示範這些變數可能會在 Unix C 殼層 (csh) 環境中設定的方式。 在 Korn 殼層和 DOS 環境的動作是類似，，如下所示：  
  
 csh:  
 setenv OMP_SCHEDULE [動態]  
  
 ksh:  
 匯出 OMP_SCHEDULE = 「 動態 」  
  
 DOS:  
 設定 OMP_SCHEDULE = 「 動態 」
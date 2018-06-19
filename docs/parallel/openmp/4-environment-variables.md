---
title: 4. 環境變數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690997"
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
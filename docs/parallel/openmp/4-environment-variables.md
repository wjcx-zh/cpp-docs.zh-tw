---
title: 4. 環境變數
ms.date: 11/04/2016
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 0dec302762ad22fc3c7f6691ef63df1b07d5940d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456598"
---
# <a name="4-environment-variables"></a>4.環境變數

此章節會描述 OpenMP C 和 c + + API 的環境變數 （或對等平台特定的機制），以控制平行處理程式碼的執行。  環境變數名稱必須是大寫。 指派給它們的值不區分大小寫，且可能有前置和尾端空白字元。  修改程式啟動之後的值都會被忽略。

環境變數如下所示：

- **OMP_SCHEDULE**設定執行階段排程類型與區塊大小。

- **OMP_NUM_THREADS**設定執行期間要使用的執行緒數目。

- **OMP_DYNAMIC**啟用或停用動態調整執行緒數目。

- **OMP_NESTED**啟用或停用巢狀平行處理原則。

在這一章中的範例只示範如何在 Unix C 殼層 (csh) 環境中可能會設定這些變數。 在 Korn 殼層和 DOS 環境動作類似，如下所示：

csh: setenv OMP_SCHEDULE 「 動態 」

ksh： 匯出 OMP_SCHEDULE = 「 動態 」

DOS： 設定 OMP_SCHEDULE = 「 動態 」
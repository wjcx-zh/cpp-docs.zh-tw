---
title: 4. 環境變數 |Microsoft Docs
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
ms.openlocfilehash: aec56dad334dcd27de2068e660ff8ec5a6e72f90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415484"
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
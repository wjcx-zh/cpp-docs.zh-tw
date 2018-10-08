---
title: 經過時間： Automation 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8f36c48cf654379e9db3a99c2404732dca30f63
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860314"
---
# <a name="elapsed-time-automation-classes"></a>經過時間： Automation 類別

此程序示範如何計算兩個之間的差異`CTime`物件，以及如何取得`CTimeSpan`結果。

## <a name="to-calculate-elapsed-time"></a>若要計算經過的時間

1. 建立兩個`COleDateTime`物件。

1. 其中一個設定`COleDateTime`物件目前的時間。

1. 執行某些耗時的工作。

1. 設定其他`COleDateTime`物件目前的時間。

1. 需要兩個時間之間的差異。

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>另請參閱

[日期和時間：Automation 支援](../atl-mfc-shared/date-and-time-automation-support.md)

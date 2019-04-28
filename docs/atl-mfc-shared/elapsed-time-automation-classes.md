---
title: 經過時間：Automation 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: d6a77d57a88166354fcb222c0da09690426108e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235783"
---
# <a name="elapsed-time-automation-classes"></a>經過時間：Automation 類別

此程序示範如何計算兩個之間的差異`CTime`物件，以及如何取得`CTimeSpan`結果。

## <a name="to-calculate-elapsed-time"></a>若要計算經過的時間

1. 建立兩個`COleDateTime`物件。

1. 其中一個設定`COleDateTime`物件目前的時間。

1. 執行某些耗時的工作。

1. 設定其他`COleDateTime`物件目前的時間。

1. 需要兩個時間之間的差異。

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>另請參閱

[日期和時間：自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)

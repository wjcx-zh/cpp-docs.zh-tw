---
title: 目前時間：Automation 類別
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
ms.openlocfilehash: f1183bc5fd42a59c73556d6fdecfd45c781e8cd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236433"
---
# <a name="current-time-automation-classes"></a>目前時間：Automation 類別

下列程序示範如何建立`COleDateTime`物件，並將它初始化與目前的時間。

## <a name="to-get-the-current-time"></a>若要取得目前的時間

1. 建立 `COleDateTime` 物件。

1. 呼叫 `GetCurrentTime`。

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>另請參閱

[日期和時間：自動化支援](../atl-mfc-shared/date-and-time-automation-support.md)

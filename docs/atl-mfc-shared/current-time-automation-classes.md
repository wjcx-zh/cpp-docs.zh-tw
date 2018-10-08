---
title: 目前的時間： Automation 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, COleDateTime object
- procedures, getting current time
- Automation classes, current time
- time, getting current
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ead35da3c20630e93757787f54755dd383264d2
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860611"
---
# <a name="current-time-automation-classes"></a>目前的時間： Automation 類別

下列程序示範如何建立`COleDateTime`物件，並將它初始化與目前的時間。

## <a name="to-get-the-current-time"></a>若要取得目前的時間

1. 建立 `COleDateTime` 物件。

1. 呼叫 `GetCurrentTime`。

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

## <a name="see-also"></a>另請參閱

[日期和時間：Automation 支援](../atl-mfc-shared/date-and-time-automation-support.md)

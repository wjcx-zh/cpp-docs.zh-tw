---
title: 安卓調試器屬性 (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374205"
---
# <a name="android-debugger-properties"></a>Android 偵錯工具屬性

| 屬性 | 描述 | Choices |
|--|--|--|
| 偵錯工具類型 | 指定要偵錯的程式碼類型。 | **僅限本機**<br /><br />**僅限 Java** |
| 偵錯目標 | 指定要用於偵錯的模擬器或裝置。 如果沒有模擬器運行,則使用「Android 虛擬設備 (AVD) 管理器」啟動設備。 |
| 要啟動的套件 | 指定將除錯的 *.apk*的位置。 當除錯應用程式時,這個選項啟動包 (APK)。 |
| 啟動活動 | 您用於啟動應用程式的 Android 活動必須與資訊清單中所使用的活動相符。 按"應用"從*AndroidManifest.xml*檢索列表並動態填充它。 |
| 其他符號搜尋路徑 | 偵錯符號的其他搜尋路徑。 |
| Java 原始程式檔的其他搜尋路徑 | Java 原始程式檔的其他搜尋路徑  (僅適用於當偵錯工具類型為僅限 Java 時)。 |

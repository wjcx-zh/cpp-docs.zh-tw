---
title: Android 偵錯工具屬性C++（）
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 3ac896b384181e4e2b436368f39a343d35fe321a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446891"
---
# <a name="android-debugger-properties"></a>Android 偵錯工具屬性

| 屬性 | 描述 | Choices |
|--|--|--|
| 偵錯工具類型 | 指定要偵錯的程式碼類型。 | **僅限原生**<br /><br />**僅限 Java** |
| 偵錯目標 | 指定要用於偵錯的模擬器或裝置。 如果沒有模擬器正在執行，則使用 [Android 虛擬裝置（AVD）管理員] 來啟動裝置。 |
| 要啟動的套件 | 指定將進行偵錯的 *.apk* 位置。 此選項會在應用程式進行調試時啟動封裝（APK）。 |
| 啟動活動 | 您用於啟動應用程式的 Android 活動必須與資訊清單中所使用的活動相符。 按 [套用] 以從 *AndroidManifest.xml* 擷取清單並動態填入。 |
| 其他符號搜尋路徑 | 偵錯符號的其他搜尋路徑。 |
| Java 原始程式檔的其他搜尋路徑 | Java 原始程式檔的其他搜尋路徑 (僅適用於當偵錯工具類型為僅限 Java 時)。 |

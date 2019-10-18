---
title: 在 Visual Studio 中設定 CMake 偵錯工作階段
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 41f53c0c3ea46a8a1aa11215968aaee6c13c2dea
ms.sourcegitcommit: e33126222c418daf977533ea9e2819d99e0d7b8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534113"
---
# <a name="configure-cmake-debugging-sessions"></a>設定 CMake 偵錯工作階段

[一般] 工具列的 [啟動項目] 下拉式清單中會顯示所有可執行的 CMake 目標。 若要啟動偵錯工作階段，只要選取其中一個目標並啟動偵錯工具即可。

![CMake 啟始專案下拉式清單](media/cmake-startup-item-dropdown.png "CMake 啟始專案下拉式清單")

您也可以從方案總管啟動 debug 會話。 首先，切換至 [**方案總管**] 視窗中的 [ **CMake 目標**]。

![CMake 目標視圖按鈕](media/cmake-targets-view.png  "CMake 目標 View 功能表項目")

然後，在任何可執行檔上按一下滑鼠右鍵，然後選取 [ **debug** ] 或 [ **Debug and 啟動設定**]。 [ **Debug** ] 會根據您的使用中設定，自動開始對選取的目標進行偵錯工具。 [**偵錯工具和啟動設定**] 會開啟 [*啟動檔案與 json*檔案]，並為選取的目標加入新的 [debug] 設定。

## <a name="customize-debugger-settings"></a>自訂偵錯工具設定

若要自訂您專案中任何可執行 CMake 目標的偵錯工具設定，請以滑鼠右鍵按一下特定 CMakeLists.txt 檔案，然後選取 [偵錯並啟動設定]。 （或在**方案總管**中選取 [目標]**視圖**中的目標）。當您在子功能表中選取 CMake 目標時，會建立名為 [**啟動. vs. json** ] 的檔案。 此檔案會預先填入您已選取之 CMake 目標的相關資訊，並可讓您指定其他參數，例如程式引數或偵錯工具類型。 若要參考**CMakeSettings json**檔案中的任何索引鍵，請在其前面加上**啟動. 與 json**中的 `cmake.`。 下列範例顯示簡單的**啟動檔案與 json**檔案，該檔案會針對目前選取的設定，提取**CMakeSettings**中 `remoteCopySources` 機碼的值：

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

一旦您儲存了**vs json**檔案，就會在 [**啟動專案**] 下拉式清單中建立具有新名稱的專案。 藉由編輯**啟動檔案與 json**檔案，您可以針對任意數量的 CMake 目標，建立您想要的多個偵錯工具設定。

## <a name="support-for-cmakesettings-variables"></a>CMakeSettings 變數支援

 [**啟動]： [vs. json** ] 支援在**CMakeSettings**中宣告的變數（如下所示），並適用于目前選取的設定。 它也有一個名為 `currentDir` 的索引鍵，它會為本機專案設定啟動應用程式的目前目錄：

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

當您執行應用程式時，`currentDir` 的值會類似於

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

金鑰 ' cwd ' 會為遠端專案設定啟動應用程式的目前目錄。 預設值為 ' $ {debugInfo. System.defaultworkingdirectory} '，其評估為 

```cmd
/var/tmp/src/bfc6f7f4-4f0f-8b35-80d7-9198fa973fb9/Linux-Debug
```

## <a name="see-also"></a>請參閱

[CMake Projects in Visual Studio](cmake-projects-in-visual-studio.md) (Visual Studio 中的 CMake 專案)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自訂 CMake 建置設定](customize-cmake-settings.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake 預先定義組態參考](cmake-predefined-configuration-reference.md)<br/>

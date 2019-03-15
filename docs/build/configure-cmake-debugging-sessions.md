---
title: 設定偵錯工作階段在 Visual Studio 中的 CMake
ms.date: 03/05/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 9a4dd009544a4590c336697ba2162eec45718869
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826077"
---
# <a name="configure-cmake-debugging-sessions"></a>設定 CMake 偵錯工作階段

[一般] 工具列的 [啟動項目] 下拉式清單中會顯示所有可執行的 CMake 目標。 若要啟動偵錯工作階段，只要選取其中一個目標並啟動偵錯工具即可。

![CMake 啟動項目下拉式清單](media/cmake-startup-item-dropdown.png "CMake 啟動項目下拉式清單")

您也可以從 [CMake] 功能表啟動偵錯工作階段。

## <a name="customize-debugger-settings"></a>自訂偵錯工具設定

若要自訂您專案中任何可執行 CMake 目標的偵錯工具設定，請以滑鼠右鍵按一下特定 CMakeLists.txt 檔案，然後選取 [偵錯並啟動設定]。 當您在子功能表中選取 CMake 目標時，檔案稱為`launch.vs.json`建立。 此檔案會預先填入您已選取之 CMake 目標的相關資訊，並可讓您指定其他參數，例如程式引數或偵錯工具類型。 若要參考中的任何索引鍵`CMakeSettings.json`檔案中前, 加上與其`cmake.`在`launch.vs.json`。 下列範例顯示簡單`launch.vs.json`提取的值中的檔案`remoteCopySources`中的索引鍵`CMakeSettings.json`目前選取的組態檔：

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

當您儲存`launch.vs.json`檔案中，會建立一個項目**啟動項目**下拉式清單中，使用新的名稱。 藉由編輯`launch.vs.json`檔案中，您可以建立許多偵錯組態，因為喜歡的任意數目的 CMake 目標。

## <a name="support-for-cmakesettings-variables"></a>發生 CMakeSettings 變數的支援

 `Launch.vs.json` 支援以宣告的變數`CMakeSettings.json`（如下所示） 和適用於目前選取的組態。 它也具有名為索引鍵`currentDir`，可設定的啟動應用程式目前的目錄：

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
## <a name="see-also"></a>另請參閱

[Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)<br/>
[設定 Linux CMake 專案](../linux/cmake-linux-project.md)<br/>
[連線到遠端 Linux 電腦](../linux/connect-to-your-remote-linux-computer.md)<br/>
[自訂 CMake 建置設定](customize-cmake-settings.md)<br/>
[設定 CMake 偵錯工作階段](configure-cmake-debugging-sessions.md)<br/>
[部署、執行及偵錯 Linux 專案](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[預先定義的 CMake 組態參考](cmake-predefined-configuration-reference.md)<br/>
---
title: C++調試屬性頁
ms.date: 7/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: a63ac181b4ef281d6d78d951a46bba85103ba636
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537794"
---
# <a name="c-debugging-property-pages"></a>C++調試屬性頁

這些屬性頁位於 [**專案** > **屬性** > ] [設定] [**屬性** > ] [設定] 下。 在下拉式控制項中選擇偵錯工具類型。 如需調試C++程式碼的詳細資訊[, 請參閱教學課程:瞭解如何使用C++ Visual Studio](/visualstudio/debugger/getting-started-with-the-debugger-cpp)和[調試](/visualstudio/debugger/debugging-native-code)程式碼來進行程式碼的偵錯工具。

## <a name="local-windows-debugger-property-page"></a>本機 Windows 偵錯工具屬性頁

### <a name="command"></a>命令

要執行的偵錯命令。

### <a name="command-arguments"></a>命令引數

要傳遞至應用程式的命令列引數。

### <a name="working-directory"></a>工作目錄

應用程式的工作目錄。 根據預設, 包含專案檔案的目錄。

### <a name="attach"></a>附加

指定偵錯工具啟動時, 是否應該嘗試附加至現有的進程。

### <a name="debugger-type"></a>偵錯工具類型

指定要使用的偵錯工具類型。 當設定為 [自動] 時, 會根據 exe 檔案的內容來選取偵錯工具類型。

**做**

- **僅限原生**-僅限原生
- 僅**限 managed** -僅限受控
- **混合**混合
- **自動**-自動
- **腳本**-腳本
- **僅限 GPUC++ (amp)** -僅限C++ gpu (amp)

### <a name="environment"></a>環境

指定要進行偵錯工具的環境, 或要與現有環境合併的變數。

### <a name="debugging-accelerator-type"></a>調試快速鍵類型

用於偵測 GPU 程式碼的偵錯工具加速器類型。 (當 GPU 偵錯工具作用中時, 可使用)。

### <a name="gpu-default-breakpoint-behavior"></a>GPU 預設中斷點行為

設定 GPU 偵錯工具中斷的頻率。

**做**

- 每次扭曲一次就**中斷一次**
- 針對每個執行緒 (例如 cpu 行為 **) 中斷**每個執行緒 (例如 cpu 行為)

### <a name="merge-environment"></a>合併環境

合併指定的環境變數與現有的環境。

### <a name="sql-debugging"></a>SQL 偵錯

附加 SQL 偵錯工具。

### <a name="amp-default-accelerator"></a>AMP 的預設加速器

覆C++寫 AMP 的預設加速器選取專案。 當偵錯工具代碼時, 不適用屬性。

## <a name="remote-windows-debugger-property-page"></a>遠端 Windows 偵錯工具屬性頁

如需遠端偵錯程式的詳細資訊, 請參閱[Visual Studio C++中的遠端偵錯程式的視覺化專案](/visualstudio/debugger/remote-debugging-cpp)。

### <a name="remote-command"></a>遠端命令

要執行的偵錯命令。

### <a name="remote-command-arguments"></a>選端命令引數

要傳遞至應用程式的命令列引數。

### <a name="working-directory"></a>工作目錄

應用程式的工作目錄。 根據預設, 包含專案檔案的目錄。

### <a name="remote-server-name"></a>遠端伺服器名稱

指定遠端伺服器名稱。

### <a name="connection"></a>連線

指定連線類型。

**做**

- **遠端使用 windows 驗證**-遠端使用[windows 驗證](/windows-server/security/windows-authentication/windows-authentication-overview)。
- **不具驗證的遠端**-不含驗證的遠端。

### <a name="debugger-type"></a>偵錯工具類型

指定要使用的偵錯工具類型。 當設定為 [自動] 時, 會根據 exe 檔案的內容來選取偵錯工具類型。

**做**

- **僅限原生**-僅限原生
- 僅**限 managed** -僅限受控
- **混合**混合
- **自動**-自動
- **腳本**-腳本
- **僅限 GPUC++ (amp)** -僅限C++ gpu (amp)

### <a name="environment"></a>環境

指定要進行偵錯工具的環境, 或要與現有環境合併的變數。

### <a name="debugging-accelerator-type"></a>調試快速鍵類型

用於偵測 GPU 程式碼的偵錯工具加速器類型。 (當 GPU 偵錯工具作用中時, 可使用)。

### <a name="gpu-default-breakpoint-behavior"></a>GPU 預設中斷點行為

設定 GPU 偵錯工具中斷的頻率。

**做**

- 每次扭曲一次就**中斷一次**
- 針對每個執行緒 (例如 cpu 行為 **) 中斷**每個執行緒 (例如 cpu 行為)

### <a name="attach"></a>附加

指定偵錯工具啟動時, 是否應該嘗試附加至現有的進程。

### <a name="sql-debugging"></a>SQL 偵錯

附加 SQL 偵錯工具。

### <a name="deployment-directory"></a>部署目錄

在遠端電腦上進行偵錯工具時, 如果您想要將專案輸出的內容 (PDB 檔案除外) 複製到遠端電腦, 請在這裡指定路徑。

### <a name="additional-files-to-deploy"></a>要部署的其他檔案

在遠端電腦上進行偵錯工具時, 在此處指定的檔案和目錄 (除了專案輸出之外) 會複製到部署目錄 (如果有指定的話)。

### <a name="deploy-visual-c-debug-runtime-libraries"></a>部署 Visual C++ 偵錯執行階段程式庫

指定是否要為使用中的平臺 (Win32、x64 或 ARM) 部署偵錯工具執行時間程式庫。

### <a name="amp-default-accelerator"></a>AMP 的預設加速器

覆C++寫 AMP 的預設加速器選取專案。 當偵錯工具代碼時, 不適用屬性。

## <a name="web-browser-debugger-property-page"></a>網頁瀏覽器偵錯工具屬性頁

### <a name="http-url"></a>HTTP URL

指定專案的 URL。

### <a name="debugger-type"></a>偵錯工具類型

指定要使用的偵錯工具類型。 當設定為 [自動] 時, 會根據 exe 檔案的內容來選取偵錯工具類型。

**做**

- **僅限原生**-僅限原生
- 僅**限 managed** -僅限受控
- **混合**混合
- **自動**-自動
- **腳本**-腳本

## <a name="web-service-debugger-property-page"></a>Web 服務偵錯工具屬性頁

### <a name="http-url"></a>HTTP URL

指定專案的 URL。

### <a name="debugger-type"></a>偵錯工具類型

指定要使用的偵錯工具類型。 當設定為 [自動] 時, 會根據 exe 檔案的內容來選取偵錯工具類型。

**做**

- **僅限原生**-僅限原生
- 僅**限 managed** -僅限受控
- **混合**混合
- **自動**-自動
- **腳本**-腳本

### <a name="sql-debugging"></a>SQL 偵錯

附加 SQL 偵錯工具。
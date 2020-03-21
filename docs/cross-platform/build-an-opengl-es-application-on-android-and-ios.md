---
title: 在 Android 和 iOS 上建置 OpenGL ES 應用程式
ms.date: 10/09/2019
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
ms.openlocfilehash: 3709cfcc681f265d08758f97422ae16e98a66a1c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079662"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>在 Android 和 iOS 上建置 OpenGL ES 應用程式

您可以針對共用通用程式碼的 iOS 應用程式與 Android 應用程式，建立 Visual Studio 方案和專案。 這篇文章會引導您完成結合的解決方案範本。 它會建立 iOS 應用程式和 Android Native Activity 應用程式。 這兩個應用程式有通用的 C++ 程式碼，該程式碼使用 OpenGL ES 在每個平台上顯示相同的動畫旋轉立方體。 OpenGL ES （適用于 Embedded 系統或 GLES 的 OpenGL）是2D 和3D 圖形 API。 這在許多行動裝置上都受到支援。

## <a name="requirements"></a>需求

符合所有系統需求，以建立適用于 iOS 和 Android 的 OpenGL ES 應用程式。 否則，請安裝 Visual Studio Installer 中的「使用 C++ 進行行動開發」工作負載。 若要取得 OpenGL ES 範本，以及針對 iOS 建立，請包含選用C++的 ios 開發工具。 若要建立 Android，請安裝C++ android 開發工具和必要的協力廠商工具： android NDK、Apache Ant 和 Google Android Emulator。

為了讓 Intel 平臺上的模擬器效能更佳，其中一個選項是安裝 Intel Hardware Accelerated Execution Manager （HAXM）。 如需詳細指示，請參閱[使用C++安裝跨平臺](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)行動裝置開發。

若要建立和測試 iOS 應用程式，您需要 Mac 電腦。 根據安裝指示進行設定。 如需如何設定 iOS 開發環境的詳細資訊，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。

## <a name="create-a-new-opengles-application-project"></a>建立新的 OpenGLES 應用程式專案

在本教學課程中，您會先建立新的 OpenGL ES 應用程式專案。 然後在 Android 模擬器中建立並執行預設應用程式。 接下來，您會建置適用於 iOS 的應用程式，然後在 iOS 裝置上執行該應用程式。

::: moniker range="vs-2017"

1. 在 Visual Studio 中，**選擇 [** 檔案 >**新增**>**專案**]。

1. 在 [**新增專案**] 對話方塊的 [**範本**] 底下，選擇 [  **C++ Visual** >**跨平臺**]，然後選擇 [ **OpenGLES 應用程式（Android、iOS）** ] 範本。

1. 提供應用程式的名稱，例如*myopenglesapp.shared*，然後選擇 **[確定]** 。

   ![新增 OpenGLES 應用程式專案](../cross-platform/media/cppmdd-opengles-newproj.png "新的 OpenGLES 應用程式專案")

   Visual Studio 會建立新的方案，並開啟方案總管。

   ![方案總管中的 Myopenglesapp.shared](../cross-platform/media/cppmdd-opengles-solexpl.png "方案總管中的 MyOpenGLESApp")

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，**選擇 [** 檔案 >**新增**>**專案**]。

1. 在 [**建立新專案**] 對話方塊中，選取 [ **OpenGLES 應用程式（Android、iOS）** ] 範本，然後選擇 [**下一步]** 。

1. 在 [**設定您的新專案**] 對話方塊中，于 [**專案名稱**] 中輸入*myopenglesapp.shared*之類的名稱，然後選擇 [**建立**]。

   Visual Studio 會建立新的方案，並開啟方案總管。

   ![方案總管中的 Myopenglesapp.shared](../cross-platform/media/cppmdd-opengles-solexpl.png "方案總管中的 MyOpenGLESApp")

::: moniker-end

新的 OpenGL ES 應用程式方案包含三個程式庫專案和兩個應用程式專案。 [程式庫] 資料夾包含共用程式碼專案。 另外，還有兩個參考共用程式碼的平臺特定專案：

- `MyOpenGLESApp.Android.NativeActivity` 包含參考和黏附程式碼，可讓您的應用程式當作 Native Activity 在 Android 上實作。 黏附程式碼的進入點是在 *main.cpp* 中實作的，其中包含 `MyOpenGLESApp.Shared` 中共用的通用程式碼。 先行編譯標頭檔位於 *pch.h* 中。 這個 Native Activity 應用程式專案會編譯至  *專案所挑選的共用程式庫 (* .so`MyOpenGLESApp.Android.Packaging`) 檔案中。

- `MyOpenGLESApp.iOS.StaticLibrary` 會建立 iOS 靜態程式庫 ( *.a*) 檔案，其中包含 `MyOpenGLESApp.Shared`中的共用程式碼。 它會連結到由 `MyOpenGLESApp.iOS.Application` 專案所建立的應用程式。

- `MyOpenGLESApp.Shared` 包含可跨平台運作的共用程式碼。 它使用前置處理器巨集來進行平台專屬程式碼的條件式編譯。 共用程式碼會由 `MyOpenGLESApp.Android.NativeActivity` 與 `MyOpenGLESApp.iOS.StaticLibrary` 中的專案參考挑選。

該方案包含兩個專案，分別為 Android 和 iOS 平台建置應用程式：

- `MyOpenGLESApp.Android.Packaging` 會建立部署在 Android 裝置或模擬器上時所使用的 *.apk* 檔案。 此檔案中包含資源以及您設定資訊清單屬性所在的 AndroidManifest.xml 檔案。 其中也包含用來控制建置流程的 *build.xml* 檔案。 根據預設，它會設定為啟始專案，以便直接從 Visual Studio 部署及執行。

- `MyOpenGLESApp.iOS.Application` 包含 resources 和目標-C 的粘合程式碼，以建立連結至 `MyOpenGLESApp.iOS.StaticLibrary`中C++靜態程式庫程式碼的 iOS 應用程式。 這個專案會建立組建套件，並由 Visual Studio 和遠端代理程式傳輸到您的 Mac。 當您建置這個專案時，Visual Studio 會傳送檔案和命令，以在 Mac 上建置及部署應用程式。

## <a name="build-and-run-the-android-app"></a>建置並執行 Android 應用程式

範本所建立的方案會將 Android 應用程式設定為預設專案。  您可以建置並執行這個應用程式，以確認您的安裝和設定。 針對初始測試，在 Android 版模擬器安裝的其中一個裝置設定檔上執行應用程式。 如果您想要在其他目標上測試您的應用程式，您可以載入目標模擬器。 或者，將裝置連接到您的電腦。

### <a name="to-build-and-run-the-android-native-activity-app"></a>建置並執行 Android Native Activity 應用程式

1. 如果尚未選取，請從 [方案平台] 下拉式清單中選擇 [x86]。

   ![將方案平臺設定為 x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "將方案平台設定為 x86")

   使用 x86 將目標設定為模擬器。 若要將目標設定為裝置，請根據裝置處理器來選擇方案平台。 如果未顯示 [方案平台] 清單，請從 [新增或移除按鈕] 清單中選擇 [方案平台]，然後選擇您的平台。

1. 在 [方案總管] 中，開啟 `MyOpenGLESApp.Android.Packaging` 專案的捷徑功能表，然後選擇 [建置]。

   ![建立 Android 封裝專案](../cross-platform/media/cppmdd-opengles-andbuild.png "建置 Android 封裝專案")

   [輸出] 視窗會顯示 Android 共用程式庫和 Android 應用程式的建置流程輸出。

   ![Android 專案的組建輸出](../cross-platform/media/cppmdd-opengles-andoutput.png "建置 Android 專案輸出")

1. 選擇其中一個模擬的 Android 裝置設定檔作為部署目標。

   ![選擇部署目標](../cross-platform/media/cppmdd-opengles-pickemulator.png "選擇部署目標")

   您可能已安裝其他模擬器或連接 Android 裝置。 您可以在 [部署目標] 下拉式清單中選擇它們。 若要執行應用程式，所建置的方案平台必須符合目標裝置的平台。

1. 按**f5**開始進行調試，或按**Shift**+**F5**啟動而不進行調試。

   Visual Studio 會啟動模擬器，這需要幾秒的時間來載入及部署您的程式碼。 以下是應用程式出現在模擬器中的方式：

   ![在 Android Emulator 中執行的應用程式](../cross-platform/media/cppmdd-opengles-andemulator.png "在 Android 模擬器中執行的應用程式")

   在您的應用程式啟動之後，您可以設定中斷點，並使用偵錯工具，以逐步執行程式碼、檢查本機及監看值。

1. 按 **Shift**+**F5** 停止偵錯。

   模擬器是分開的程序，會繼續執行。 您可以將程式碼多次編輯、編譯及部署至相同的模擬器。 您的應用程式會出現在模擬器的應用程式集合中，並可由此直接啟動。

   產生的 Android Native Activity 應用程式和程式庫專案C++會將共用程式碼放在動態連結程式庫中。 其中包含「粘連」程式碼，可與 Android 平臺互動。 大部分的應用程式程式碼都位於程式庫中。 資訊清單、資源和組建指示位於封裝專案中。 共用程式碼會從 NativeActivity 專案中的 main.cpp 呼叫。 如需如何對 Android Native Activity 進行程式設計的詳細資訊，請參閱 Android 開發人員 NDK 的 [概念](https://developer.android.com/ndk/guides/concepts.html) 頁面。

   Visual Studio 使用 Android NDK 建立 Android Native Activity 專案。 它會使用 Clang 作為平臺工具組。 Visual Studio 會將專案的屬性對應至目標平臺上的編譯、連結和偵錯工具命令。 如需詳細資料，請開啟 MyOpenGLESApp.Android.NativeActivity 專案的 [屬性頁] 對話方塊。 如需有關命令列參數的詳細資訊，請參閱 [Clang Compiler 使用者手冊](https://clang.llvm.org/docs/UsersManual.html)。

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>在 iOS 裝置上建置並執行 iOS 應用程式

您可以在 Visual Studio 中建立和編輯 iOS 應用程式專案。 由於授許可權制，必須從 Mac 建立和部署。 Visual Studio 會與 Mac 上所執行的遠端代理程式通訊，以傳輸專案檔，並執行建置、部署和偵錯命令。 安裝並設定 Mac 和 Visual Studio 以進行通訊，才能建置 iOS 應用程式。 如需詳細指示，請參閱[安裝和設定工具以使用 iOS 進行建置](../cross-platform/install-and-configure-tools-to-build-using-ios.md)。 在您的 Mac 上執行遠端代理程式，並將它與 Visual Studio 配對。 接著，您可以建立並執行 iOS 應用程式，以確認您的安裝和設定。

若要將您的應用程式部署至 iOS 裝置，請先在 Xcode 中設定自動登入。 自動簽署會建立布建設定檔來簽署應用程式的組建。

### <a name="to-set-up-automatic-signing-on-xcode"></a>若要在 Xcode 上設定自動簽署

1. 如果您還沒有這麼做，請在 Mac 上安裝[Xcode](https://developer.apple.com/xcode/) 。

1. 在 Mac 上開啟 Xcode 應用程式。

1. 建立一個新的**單一檢視應用程式** Xcode 專案。 在專案建立期間填寫必填欄位。 這些值可以是任意的，因為專案僅用於建立稍後用來簽署應用程式組建的佈建設定檔。

1. 將您在 [Apple Developer Program](https://developer.apple.com/programs/) 帳戶中註冊的 Apple ID 加入到 Xcode 中。 您的 Apple ID 會當作簽署應用程式的簽署身分識別使用。 若要在 Xcode 中新增簽署身分識別，請開啟 [Xcode] 功能表，並選擇 [喜好設定]。 選取 [帳戶]，然後按一下 [新增] 按鈕 (+) 來新增您的 Apple ID。 如需詳細指示，請參閱[新增您的 Apple ID 帳戶](https://help.apple.com/xcode/mac/current/#/devaf282080a) \(英文\)。

1. 從 Xcode 專案的 [一般] 設定中，將 [套件組合識別碼] 的值變更為 `com.<NameOfVSProject>`，其中 `<NameOfVSProject>` 是與您所建立的 Visual Studio 方案專案相同的名稱。 例如，如果您在 Visual Studio 上建立一個稱為 `MyOpenGLESApp` 的專案，則將 [套件組合識別碼] 設定為 `com.MyOpenGLESApp`。

   ![Xcode 套件組合識別碼](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "Xcode 套件組合識別碼")

1. 若要啟用自動簽署，請核取。 自動管理簽署**。

   ![Xcode 自動簽署](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "Xcode 自動簽署")

1. 選取您當作開發**小組**新增之 Apple ID 的小組名稱。

   ![Xcode 小組](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "Xcode 小組")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>若要在 iOS 裝置上建置並執行 iOS 應用程式

1. 在 Mac 上執行遠端代理程式，並確認 Visual Studio 已與遠端代理程式搭配使用。 若要啟動遠端代理程式，請開啟終端機應用程式視窗並輸入 `vcremote`。 如需詳細資訊，請參閱 [在 Visual Studio 中設定遠端代理程式](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS)。

   ![執行 vcremote 的 Mac 終端機視窗](../cross-platform/media/cppmdd-common-vcremote.png "執行 Vcremote 的 Mac 終端機視窗")

1. 將 iOS 裝置連接到 Mac。 當您第一次將裝置連接到電腦時，會出現一個警示，詢問您是否信任存取您裝置的電腦。 讓裝置信任 Mac 電腦。

1. 在 Visual Studio 上，根據您裝置的處理器，從 [方案平台] 下拉式清單中選擇方案平台 (如果尚未選取)。 此範例中為 **ARM64** 處理器。

   ![將方案平臺設定為 ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "將方案平臺設定為 ARM64")

1. 在 [方案總管] 中，開啟 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [卸載專案] 來卸載專案。

1. 再次開啟已卸載之 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [編輯 project.pbxproj] 來編輯專案檔。 在 `project.pbxproj` 檔案中，尋找 `buildSettings` 屬性，然後使用 Apple Team ID 新增 `DEVELOPMENT_TEAM`。 以下螢幕擷取畫面會針對 Apple Team ID 顯示 `123456ABC` 的範例值。 您可以從 Xcode 找到 Apple Team ID 的值。 移至 [組建設定]，並將滑鼠指標停留在您的開發小組名稱上，以顯示工具提示。 工具提示會顯示您的小組識別碼。

   ![設定開發小組](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "設定開發小組")

1. 關閉 `project.pbxproj` 檔案，然後開啟已卸載之 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，並選擇 [重新載入專案] 來重新載入專案。

1. 現在，開啟 MyOpenGLESApp.iOS.Application 專案的捷徑功能表，然後選擇 [建置]，以建置該專案。

   ![組建 iOS 應用程式專案](../cross-platform/media/cppmdd-opengles-iosbuild.png "建置 iOS 應用程式專案")

   [輸出] 視窗會顯示組建進程的輸出。 它會顯示 iOS 靜態程式庫和 iOS 應用程式的結果。 在 Mac 上，執行遠端代理程式的終端機視窗會顯示命令和檔案傳輸活動。

   在 Mac 電腦上，系統可能會提示您允許 Codesign 存取您的 Keychain。 選擇 [允許] 繼續進行。

1. 在工具列上選擇您的 iOS 裝置，以便在連接到 Mac 的裝置上執行應用程式。 如果應用程式未啟動，請確認裝置是否授予已部署的應用程式在裝置上執行的權限。 您可以前往裝置上的 [設定] > [一般] > [裝置管理] 來設定此權限。 選取您的開發人員應用程式帳戶、信任您的帳戶，然後驗證應用程式。 再次嘗試從 Visual Studio 執行應用程式。

   ![iOS 裝置上的 iOS 應用程式](../cross-platform/media/cppmdd-opengles-iosdevice.png "iOS 裝置上的 iOS 應用程式")

   在您的應用程式啟動之後，您可以設定中斷點，並使用 Visual Studio 偵錯工具來檢查區域變數、查看呼叫堆疊及監看值。

   ![IOS 應用程式中中斷點處的偵錯工具](../cross-platform/media/cppmdd-opengles-iosdebug.png "位於 iOS 應用程式中斷點上的偵錯工具")

1. 按 **Shift**+**F5** 停止偵錯。

   產生的 iOS 應用程式和程式庫專案會將 C++ 程式碼放在只實作共用程式碼的靜態程式庫中。 大多數應用程式程式碼會位於 `Application` 專案中。 對這個範本專案中之共用程式庫程式碼的呼叫會在 *GameViewController.m* 檔案中進行。 為了建置您的 iOS 應用程式，Visual Studio 使用 Xcode 平台工具組，該工具組需要與 Mac 上所執行的遠端用戶端進行通訊。

   Visual Studio 將專案檔案傳送至遠端用戶端。 然後，它會傳送命令以使用 Xcode 建立應用程式。 遠端用戶端會將組建狀態資訊傳回 Visual Studio。 當應用程式成功建立時，Visual Studio 可以傳送命令來執行和偵錯工具。 Visual Studio 中的偵錯工具可控制在連接至 Mac 的 iOS 裝置上所執行的應用程式。 Visual Studio 將專案屬性對應至目標 iOS 平臺上用來編譯、連結和調試的選項。 如需編譯器命令列選項詳細資料，請開啟 MyOpenGLESApp.iOS.StaticLibrary 專案的 [屬性頁] 對話方塊。

## <a name="customize-your-apps"></a>自訂您的應用程式

您可以修改共用的 C++ 程式碼，加入或變更一般常見功能。 變更 `MyOpenGLESApp.Android.NativeActivity` 和 `MyOpenGLESApp.iOS.Application` 專案中共用程式碼的呼叫以符合。 您可以使用前置處理器巨集，來指定通用程式碼中的平台專屬區段。 當您針對 Android 建置時，系統會預先定義前置處理器巨集 `__ANDROID__` 。 當您針對 iOS 建置時，系統會預先定義前置處理器巨集 `__APPLE__` 。

若要查看特定專案平臺的 IntelliSense，請在 [內容切換器] 下拉式清單中選擇專案。 它位於編輯器視窗頂端的巡覽列中。

![編輯器中的專案內容切換器下拉式清單](../cross-platform/media/cppmdd-opengles-contextswitcher.png)

目前專案所使用之程式碼中的 IntelliSense 問題會以紅色波浪線標示。 其他專案中的紫色波浪線標示問題。 Visual Studio 不支援 Java 或 Objective-C 檔案的程式碼顏色標示或 IntelliSense。 不過，您仍然可以修改來源檔案和資源。 使用它們來設定您的應用程式名稱、圖示和其他的執行詳細資料。

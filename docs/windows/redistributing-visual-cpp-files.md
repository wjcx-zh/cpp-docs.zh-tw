---
title: 轉散發 Visual C++ 檔案
description: Visual Studio 包括可轉散發程式庫和您可以隨應用程式部署的元件。
ms.date: 07/16/2020
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 7a639f7ad7deb76cade47b0162012dcb70cb0d69
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446749"
---
# <a name="redistributing-visual-c-files"></a>轉散發 Visual C++ 檔案

> [!NOTE]
> 這是因為您想要下載其中一個 Visual C++ 執行時間檔案嗎？ 移至[Microsoft 網站](https://www.microsoft.com/)，並在搜尋方塊中輸入**Visual C++** 可轉散發套件。 下載並安裝電腦架構的可轉散發套件 (例如，如果您執行 64 位元 Windows，則為 x64) 以及您所需的 Visual C++ 版本 (例如 2015)。

## <a name="redistributable-files-and-licensing"></a>可轉散發檔案和授權

當您部署應用程式時，您也必須部署必要的支援檔案。 如果 Microsoft 提供任何這些檔案，請檢查您是否允許重新發佈這些檔案。 您會在 IDE 中找到 Visual Studio 授權條款的連結。 使用 [關於 Microsoft Visual Studio] 對話方塊中的 [授權條款] 連結。 或者，從 Visual Studio[授權目錄](https://visualstudio.microsoft.com/license-terms/)下載相關的 eula 和授權。

::: moniker range="vs-2019"

若要查看 Visual Studio 2019 Microsoft 軟體授權條款之「可散發程式碼」一節中所參考的「可轉散發套件清單」，請參閱 Microsoft Visual Studio 2019 的可散發[程式碼](/visualstudio/releases/2019/redistribution#-distributable-code-files-for-visual-studio-2019)檔案

::: moniker-end

::: moniker range="vs-2017"

若要查看 Visual Studio 2017 Microsoft 軟體授權條款之「可散發程式碼」一節中所參考的「可轉散發套件清單」，請參閱 Microsoft Visual Studio 2017 的可散發[程式碼](/visualstudio/productinfo/2017-redistribution-vs#-distributable-code-files-for-visual-studio-2017)檔案。

::: moniker-end

::: moniker range="vs-2015"

若要查看 Visual Studio 2015 Microsoft 軟體授權條款之「可散發程式碼」一節中所參考的「可轉散發套件清單」，請參閱 Microsoft Visual Studio 2015 的可散發[程式碼](/visualstudio/productinfo/2015-redistribution-vs#-distributable-code-files-for-visual-studio-2015)檔案。

::: moniker-end

如需可轉散發檔案的詳細資訊，請參閱[決定要轉散發哪些 dll](determining-which-dlls-to-redistribute.md)和[部署範例](deployment-examples.md)。

## <a name="locate-the-redistributable-files"></a>找出可轉散發檔案

若要部署可轉散發檔案，您可以使用 Visual Studio 所安裝的可轉散發套件。 在2017之後的 Visual Studio 版本中，這些檔案會命名為 *`vc_redist.arm64.exe`* 、 *`vc_redist.x64.exe`* 和 *`vc_redist.x86.exe`* 。 在 Visual Studio 2015、Visual Studio 2017 及 Visual Studio 2019 中，它們也可以在名稱 *`vcredist_x86.exe`* 、和下取得 *`vcredist_x64.exe`* *`vcredist_arm.exe`* （僅限2015）。

尋找可轉散發檔案最簡單的方式，就是使用在開發人員命令提示字元中設定的環境變數。 在 Visual Studio 2019 的最新版本中，您可以在資料夾中找到可轉散發檔案 *`%VCINSTALLDIR%Redist\MSVC\v142`* 。 在 Visual Studio 2017 和 Visual Studio 2019 中，它們也可以在中找到 *`%VCToolsRedistDir%`* 。 在 Visual Studio 2015 中，可以在中找到這些檔案 *`%VCINSTALLDIR%redist\<locale>`* ，其中是可轉散發套件的地區設定 *`<locale>`* 。

另一個部署選項是使用可轉散發合併模組（檔案 *`.msm`* ）。 在 Visual Studio 2019 中，這些檔案是 Visual Studio 安裝程式中選擇性可安裝元件的一部分，名為**c + + 2019**可轉散發套件 msm。 在 Visual Studio 2017 和 Visual Studio 2015 中，合併模組預設會安裝為 c + + 安裝的一部分。 安裝在最新版本的 Visual Studio 2019 時，您會在中找到可轉散發合併模組 *`%VCINSTALLDIR%Redist\MSVC\v142\MergeModules`* 。 在 Visual Studio 2019 和 Visual Studio 2017 中，它們也可以在中找到 *`%VCToolsRedistDir%MergeModules`* 。 在 Visual Studio 2015 中，可以在中找到它們 *`Program Files [(x86)]\Common Files\Merge Modules`* 。

## <a name="install-the-redistributable-packages"></a>安裝可轉散發套件

Visual C++ 可轉散發套件會安裝並註冊所有 Visual C++ 程式庫。 如果您使用其中一個，請在安裝應用程式之前，先在目標系統上將其做為先決條件執行。 建議您使用這些套件進行部署，以便自動更新 Visual C++ 程式庫。 如需如何使用這些套件的範例，請參閱[逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。

每個「Visual C++ 可轉散發套件」都會檢查電腦上是否有較新的版本存在。 如果找到較新的版本，就不會安裝封裝。 從 Visual Studio 2015 開始，可轉散發套件會顯示錯誤訊息，說明安裝程式失敗。 如果封裝是使用旗標執行 **`/quiet`** ，則不會顯示任何錯誤訊息。 不論是哪一種情況，Microsoft 安裝程式都會記錄錯誤，而且錯誤結果會被傳回給呼叫者。 從 Visual Studio 2015 套件開始，您可以透過檢查登錄以判斷是否已安裝較新的版本，來避免發生此錯誤。 目前已安裝的版本號碼會儲存在機 `HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\14.0\VC\Runtimes\{x86|x64|ARM}` 碼中。 Visual Studio 2015、Visual Studio 2017 和 Visual Studio 2019 的版本號碼為14.0，因為最新的可轉散發套件與2015版本的二進位相容性。 金鑰是 `ARM` 、 `x86` 或， `x64` 視平臺已安裝的 vcredist 版本而定。 （ `Wow6432Node` 只有當您在 x64 平臺上使用 Regedit 來查看已安裝的 x86 封裝版本時，才需要檢查子機碼）。版本號碼會儲存在 REG_SZ 字串值， **`Version`** 以及 **`Major`** 、 **`Minor`** 、 **`Bld`** 和 **`Rbld`** `REG_DWORD` 值的集合中。 為了避免安裝時發生錯誤，如果目前安裝的版本較新，您必須略過安裝可轉散發套件。

## <a name="install-the-redistributable-merge-modules"></a>安裝可轉散發合併模組

可轉散發合併模組必須包含在您用來部署應用程式的 Windows Installer 套件（或類似的安裝套件）中。 如需詳細資訊，請參閱[使用合併模組轉散發](redistributing-components-by-using-merge-modules.md)。 如需範例，請參閱逐步解說[：使用安裝專案部署 Visual C++ 應用程式](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。

## <a name="install-individual-redistributable-files"></a>安裝個別的可轉散發檔案

您也可以直接在*應用程式本機資料夾*中安裝可轉散發 dll。 這是包含可執行應用程式檔的資料夾。 基於服務的理由，我們不建議您使用此安裝位置。

## <a name="potential-run-time-errors"></a>可能的執行階段錯誤

如果 Windows 找不到您應用程式所需的其中一個可轉散發程式庫 Dll，可能會顯示類似下列的訊息：「這個應用程式無法啟動，因為找不到*library*.dll。 重新安裝應用程式可能會修正此問題。」

若要解決這種錯誤，請確定您的應用程式安裝程式已正確建立。 確認可轉散發程式庫已正確部署在目標系統上。 如需詳細資訊，請參閱[了解 Visual C++ 應用程式的相依性](understanding-the-dependencies-of-a-visual-cpp-application.md)。

## <a name="related-articles"></a>相關文章

[使用合併模組轉散發](redistributing-components-by-using-merge-modules.md)\
描述如何使用 Visual C++ 可轉散發合併模組，將 Visual C++ 執行時間程式庫安裝為資料夾中的共用 Dll *`%windir%\system32\`* 。

[重新發佈 Visual C++ ActiveX 控制項](redistributing-visual-cpp-activex-controls.md)\
描述如何轉散發使用了 ActiveX 控制項的應用程式。

[轉散發 MFC 程式庫](redistributing-the-mfc-library.md)\
描述如何轉散發使用了 MFC 的應用程式。

[轉散發 ATL 應用程式](redistributing-an-atl-application.md)\
描述如何轉散發使用 ATL 的應用程式。 從 Visual Studio 2012 開始，就不需要適用於 aLT 的轉散發程式庫。

[部署範例](deployment-examples.md)\
示範如何部署 Visual C++ 應用程式的範例連結。

[部署桌面應用程式](deploying-native-desktop-applications-visual-cpp.md)\
介紹 Visual C++ 部署概念和技術。

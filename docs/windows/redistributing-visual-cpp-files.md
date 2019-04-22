---
title: 轉散發 Visual C++ 檔案
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 2bf4297a6c61d16c68d6a9cb893aed78b9d7609d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786174"
---
# <a name="redistributing-visual-c-files"></a>轉散發 Visual C++ 檔案

> [!NOTE]
> 您來到這裡是因為想要下載其中一個 Visual C++ 執行階段檔案嗎？ 移至[Microsoft 網站](http://www.microsoft.com/)，然後輸入**視覺化C++可轉散發套件**在搜尋方塊中。 下載並安裝電腦架構的可轉散發套件 (例如，如果您執行 64 位元 Windows，則為 x64) 以及您所需的 Visual C++ 版本 (例如 2015)。

當您部署應用程式時，您也必須部署必要的支援檔案。 如果其中有任何檔案是由 Microsoft 提供，請檢查您否有權限轉散發。 若要檢閱 Visual Studio 授權條款，請在 IDE 中，查看 [關於 Microsoft Visual Studio] 對話方塊中的 [授權條款] 連結，或下載 [Microsoft 軟體授權條款](https://visualstudio.microsoft.com/license-terms/mlt687465/)檔案。 若要檢視 Visual Studio 特定版本《Microsoft 軟體授權條款》之＜可散發程式碼＞一節所指的「可轉散發清單」，請參閱 [Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK 的可散發程式碼 (含公用程式與 BuildServer 檔案)](/visualstudio/productinfo/2017-redistribution-vs)；若是 Visual Studio 2015，請參閱 [Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK 的可散發程式碼](/visualstudio/productinfo/2015-redistribution-vs)。 如需可轉散發檔案的詳細資訊，請參閱[決定要轉散發哪些 DLL](determining-which-dlls-to-redistribute.md) 和[部署範例](deployment-examples.md)。

若要部署可轉散發 Visual C++ 檔案，您可以使用 Visual Studio 隨附的 Visual C++ 可轉散發套件 (VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe)。 在 Visual Studio 2017 中，您可以在 Program Files[ (x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_ 資料夾中找到這些檔案，其中 _edition_ 是安裝的 Visual Studio 版本，而 _lib-version_ 是要轉散發的程式庫版本。 在 Visual Studio 2015 中，您可以在 Visual Studio 安裝目錄 (位於 Program Files [(x86)]\Microsoft Visual Studio *version*\VC\redist\\*locale*\\) 中找到這些檔案。 另一個選項是使用可轉散發合併模組 (.msm 檔案)。在 Visual Studio 2017 中，您可以在 Program Files [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\Redist\\MSVC\\_lib-version_\\MergeModules\\ 資料夾中找到這些檔案。 在 Visual Studio 2015 中，您可以在 Program Files [(x86)]\Common Files\Merge Modules\\ 中找到這些檔案。 您也可以直接安裝「應用程式本機資料夾」中的可轉散發 Visual C++ DLL，此資料夾是包含您的可執行應用程式檔案的資料夾。 對於維護原因，建議您不要使用此安裝位置。

Visual C++ 可轉散發套件會安裝並註冊所有 Visual C++ 程式庫。 如果使用可轉散發套件，您必須在目標系統上執行該套件並設定為安裝應用程式的必要條件。 建議您使用這些套件進行部署，以便自動更新 Visual C++ 程式庫。 如需如何使用這些套件的範例，請參閱[逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。

每個「Visual C++ 可轉散發套件」都會檢查電腦上是否有較新的版本存在。 若發現較新的版本，則不會安裝該套件。 從 Visual Studio 2015 開始，可轉散發套件會顯示錯誤訊息，說明安裝程式失敗。 若使用 **/quiet** 旗標執行套件，則不會顯示錯誤訊息。 不論是哪一種情況，Microsoft 安裝程式都會記錄錯誤，而且錯誤結果會被傳回給呼叫者。 從 Visual Studio 2015 套件開始，您可以透過檢查登錄以判斷是否已安裝較新的版本，來避免發生此錯誤。 目前安裝的版本儲存在 HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\\_vs-version_\VC\Runtimes\\{x86|x64|ARM} 機碼中，其中 _vs-version_ 是 Visual Studio 的版本號碼 (14.0 同時表示 Visual Studio 2015 和 Visual Studio 2017，因為更新後的 2017 版可轉散發套件是與 2015 版相容的二進位檔)，至於機碼為 ARM、x86 或 x64，則視平台的已安裝 vcredist 版本而定。 (您不需要檢查 Wow6432Node 子機碼底下，除非您使用 RegEdit 檢視 x64 平台上安裝的 x86 套件版本。)版本號碼儲存在 REG_SZ 字串值 **Version** 中，也位於一組 **Major**、**Minor**、**Bld** 和 **Rbld** REG_DWORD 值中。 為了避免安裝時發生錯誤，如果目前安裝的版本較新，您必須略過安裝可轉散發套件。

如果您使用的合併模組包含 Visual C++ DLL，則必須將它包含在您用來部署應用程式的 Windows Installer 套件 (或類似的安裝套件) 中。 如需詳細資訊，請參閱[使用合併模組轉散發](redistributing-components-by-using-merge-modules.md)。 如需範例，請參閱[逐步解說：部署視覺效果C++使用安裝專案的應用程式](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，這也會示範如何使用 InstallShield Limited Edition 建立安裝套件。

## <a name="potential-run-time-errors"></a>可能的執行階段錯誤

如果 Windows 找不到任何可轉散發套件的程式庫應用程式所需的 Dll，可能會顯示類似下面的訊息：「 這個應用程式無法啟動，因為*程式庫*找不到.dll。 重新安裝應用程式可能可以解決這個問題。」

若要解決這種錯誤，請確定您的應用程式安裝程式建置程序正確無誤，且已將可轉散發程式庫正確地部署在目標系統上。 如需詳細資訊，請參閱[了解 Visual C++ 應用程式的相依性](understanding-the-dependencies-of-a-visual-cpp-application.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[使用合併模組轉散發](redistributing-components-by-using-merge-modules.md)|描述如何使用 Visual C++ 可轉散發合併模組，將 Visual C++ 執行階段程式庫安裝在 %windir%\system32\ 資料夾中作為共用的 DLL。|
|[轉散發 Visual C++ ActiveX 控制項](redistributing-visual-cpp-activex-controls.md)|描述如何轉散發使用了 ActiveX 控制項的應用程式。|
|[轉散發 MFC 程式庫](redistributing-the-mfc-library.md)|描述如何轉散發使用了 MFC 的應用程式。|
|[轉散發 ATL 應用程式](redistributing-an-atl-application.md)|描述如何轉散發使用 ATL 的應用程式。 從 Visual Studio 2012 開始，就不需要適用於 aLT 的轉散發程式庫。|
|[部署範例](deployment-examples.md)|示範如何部署 Visual C++ 應用程式的範例連結。|
|[部署傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)|介紹 Visual C++ 部署概念和技術。|
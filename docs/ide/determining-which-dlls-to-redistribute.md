---
title: 決定要轉散發哪些 DLL
ms.date: 06/08/2018
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: fdca832810312d2f36697da8fbaac539c5ce951c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452594"
---
# <a name="determining-which-dlls-to-redistribute"></a>決定要轉散發哪些 DLL

當您建置應用程式時，如果該應用程式使用 Visual Studio 所提供的程式庫 DLL，則應用程式使用者的電腦上也必須要有這些 DLL，應用程式才能執行。 因為大部分的使用者可能未安裝 Visual Studio，因此您必須為他們提供這些 Dll。 Visual Studio 可讓這些 DLL 成為您能夠包含在應用程式安裝程式中的「可轉散發檔案」。

為了使可轉散發 DLL 更容易包含在您的安裝程式中，這些 DLL 會以獨立的「可轉散發套件」形式提供。 這些是特定架構的可執行檔，使用集中部署將可轉散發檔案安裝在使用者的電腦上。 例如，vcredist\_x86.exe 會為 x86 電腦安裝 32 位元程式庫、vcredist\_x64.exe 會為 x64 電腦安裝 32 位元和 64 位元程式庫，而 vcredist\_ARM.exe 會為 ARM 電腦安裝程式庫。 由於 Microsoft 可以使用 Windows Update 服務個別更新這些程式庫，因此建議集中部署。 除了 Visual Studio 安裝中的複本，您也可以下載目前的可轉散發套件。 如需最新版與舊版工具組所支援之最新可轉散發套件的連結，請參閱[最新支援的 Visual C++ 下載](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)。 您可以在 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?LinkId=158431)搜尋「Visual C++ 可轉散發套件」，來尋找可轉散發套件的特定舊版。

您要部署之可轉散發套件的主要版本號碼必須符合用來建立應用程式的 Visual Studio 工具組版本，且次要版本必須為相同或更新版本。 Visual Studio 2017 和 Visual Studio 2015 具有相容的工具組版本號碼，這表示 Visual Studio 2017 可轉散發檔案可供使用 2015 版工具組建置的應用程式使用。 雖然它們可能相容，但不支援在透過 2017 版工具組建置的應用程式中使用 2015 版可轉散發檔案。 僅支援使用與您的工具組版本相同或更新的可轉散發套件。

在安裝程式中包含可轉散發 DLL 的另一種方式是使用「合併模組」。 這些 Microsoft 安裝程式模組隨附於您的應用程式安裝程式中，並由它進行安裝。 您可以在 \\VC\\Redist\MSVC\\*version*\\MergeModules\\ 下的 Visual Studio 安裝目錄中找到可轉散發 DLL 的合併模組。 在舊版 Visual Studio 中，您可以在 \\Program Files 或 \\Program Files (x86) 目錄的 Common Files\\Merge Modules 子目錄中找到這些檔案。 如需使用這些檔案的詳細資訊，請參閱[使用合併模組來轉散發元件](../ide/redistributing-components-by-using-merge-modules.md)。

個別可轉散發 DLL 也會隨附於 Visual Studio 的安裝中。 根據預設，它們會安裝在 Visual Studio 安裝目錄中 (位於 \\VC\\Redist\\MSVC\\*version* 資料夾)。 *version* 的數值可能代表一組通用可轉散發檔案的不同次要組建編號。 請使用這些目錄中之任何程式庫 DLL 檔案、可轉散發套件或合併模組的最新版本。 您可以透過將這些程式庫安裝在與您應用程式相同的目錄中，來使用這些程式庫進行本機部署。 由於您必須負責提供已部署應用程式的更新，因此不建議本機部署。 最好使用可轉散發套件集中部署。

若要判斷必須隨應用程式一起轉散發的 DLL，請收集應用程式所依賴的 DLL 並做成一份清單。 這些通常會列為連結器的匯入程式庫輸入。 預設會包含特定程式庫，例如 vcruntime 和通用 C 執行階段程式庫 (UCRT)。 如果您的應用程式或其相依性的其中一個使用 LoadLibrary 動態載入 DLL，該 DLL 可能不會列於連結器的輸入中。 收集動態載入之 DLL 清單的其中一個方法是在您的應用程式上執行 Dependency Walker (depends.exe)，如[了解 Visual C++ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)中所述。 不幸的是，此工具已過時，因此可能會回報找不到特定 DLL。

取得相依性清單後，請將它與 Microsoft Visual Studio 安裝目錄下 Redist.txt 檔案中的連結清單進行比較，或是與您 Visual Studio 複本《Microsoft 軟體授權條款》的＜可散發程式碼檔案＞一節中所指之可轉散發 DLL 的「可轉散發清單」進行比較。 若為 Visual Studio 2017，請參閱 [Microsoft Visual Studio 2017 的可散發程式碼 (含公用程式、擴充性及 BuildServer 檔案)](http://go.microsoft.com/fwlink/p/?linkid=823098)。 若為 Visual Studio 2015，請參閱 [Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK 的可散發程式碼 (含公用程式與 BuildServer 檔案)](http://go.microsoft.com/fwlink/p/?linkid=799794)。 若為 Visual Studio 2013，可在 [Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 的可散發程式碼](http://go.microsoft.com/fwlink/p/?LinkId=313603)線上取得此清單。

在 Visual Studio 2015 之前的 Visual Studio 版本中，C 執行階段程式庫 (CRT) 是以可轉散發 DLL 形式 msvc*version*.dll 隨附。 從 Visual Studio 2015 開始，CRT 中的函式已重構為 vcruntime 和 UCRT。 UCRT 現在是在 Windows 10 中的系統元件，由 Windows Update 管理。 所有 Windows 10 作業系統都可以使用此元件。 若要將您的應用程式部署到舊版作業系統，您也可能需要轉散發 UCRT。 Visual Studio 可轉散發檔案中包含舊版 UCRT，只能安裝在 Windows 10 之前的作業系統上，而且只有尚未安裝任何 UCRT 版本時才能安裝。 如需適用於舊版系統且可作為 Microsoft 系統更新套件安裝的 UCRT 版本，請參閱 Microsoft 下載中心的 [Windows 10 通用 C 執行階段](https://www.microsoft.com/download/details.aspx?id=48234)。

並不是 Visual Studio 中包含的檔案都可讓您轉散發；您只能轉散發 Redist.txt 或線上「REDIST 清單」中指定的檔案。 您不能轉散發偵錯版本的應用程式以及各種 Visual C++ 偵錯 DLL。 如需詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。

下表描述您的應用程式可能依賴的部分 Visual C++ DLL。

|Visual C++ 程式庫|描述|適用於|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|機器碼的執行階段程式庫。|使用一般 C 和 C++ 語言啟動和終止服務的應用程式。|
|vccorlib*version*.dll|受控碼的執行階段程式庫。|針對受控碼使用 C++ 語言服務的應用程式。|
|msvcp*version*.dll 和 msvcp*version*_*dotnumber*.dll|機器碼的 C++ Standard 程式庫。|使用 [C++ Standard 程式庫](../standard-library/cpp-standard-library-reference.md)的應用程式。|
|concrt*version*.dll|機器碼的並行執行階段程式庫。|使用[並行執行階段](../parallel/concrt/concurrency-runtime.md)的應用程式。|
|mfc*version*.dll|Microsoft Foundation Class (MFC) 程式庫。|使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)的應用程式。|
|mfc*version* *language*.dll|Microsoft Foundation Class (MFC) 程式庫資源。|使用 MFC 特定語言資源的應用程式。|
|mfc*version*u.dll|具有 Unicode 支援的 MFC 程式庫。|使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)並需要 Unicode 支援的應用程式。|
|mfcmifc80.dll|MFC Managed 介面程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)的應用程式。|
|mfcm*version*.dll|MFC Managed 程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)的應用程式。|
|mfcm*version*u.dll|具有 Unicode 支援的 MFC Managed 程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)並需要 Unicode 支援的應用程式。|
|vcamp*version*.dll|機器碼的 AMP 程式庫。|使用 [C++ AMP 程式庫](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)程式碼的應用程式。|
|vcomp*version*.dll|機器碼的 OpenMP 程式庫。|使用 [C++ OpenMP 程式庫](../parallel/openmp/openmp-in-visual-cpp.md)程式碼的應用程式。|

> [!NOTE]
> 您不再需要以個別 DLL 的形式轉散發 Active Template Library。 其功能已移至標頭和靜態程式庫。

如需如何隨應用程式一起轉散發這些 DLL 的詳細資訊，請參閱[轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)。 如需範例，請參閱[部署範例](../ide/deployment-examples.md)。

一般而言，您並不需要轉散發系統 Dll，因為它們是作業系統的一部分。 但是，還是有一些例外情形，例如當應用程式會在數個版本的 Microsoft 作業系統上執行時。 在此情況下，請務必閱讀對應的授權條款。 另外，請嘗試透過 Windows Update、Service Pack 或 Microsoft 提供的可轉散發套件，將系統 DLL 升級。

## <a name="see-also"></a>請參閱

[選擇部署方法](../ide/choosing-a-deployment-method.md)

[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)

---
title: "判斷要轉散發哪些 Dll |Microsoft 文件"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae47ec92ecea46aba5f0e1bf144a34fd5532af9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="determining-which-dlls-to-redistribute"></a>決定要轉散發哪些 DLL

當您建置的應用程式使用 Visual Studio 所提供的程式庫 Dll 時，應用程式的使用者也必須有這些 Dll 執行應用程式的電腦上。 因為大部分的使用者可能未安裝 Visual Studio，因此您必須為他們提供這些 Dll。 Visual Studio 使這些 Dll 成為*可轉散發檔案*併入您的應用程式安裝程式。

若要讓您更輕鬆地加入您的安裝程式可轉散發的 Dll，它們是可做為獨立*可轉散發套件*。 這些是使用集中部署安裝可轉散發檔案使用者的電腦上的特定架構的可執行檔。 比方說，vcredist\_x86.exe 安裝 32 位元程式庫適用於 x86 電腦、 vcredist\_x64.exe 會安裝 32 位元和 64 位元程式庫適用於 x64 電腦，且 vcredist\_ARM.exe arm 安裝的程式庫電腦。 我們建議集中部署，因為 Microsoft 可以使用 Windows Update 服務個別更新這些程式庫。 除了 Visual Studio 安裝中的複本，目前的可轉散發套件可供下載[VisualStudio.com/Downloads](https://www.visualstudio.com/downloads/)在其他工具及架構 > 一節。

您部署的可轉散發套件的主要版本號碼必須符合用來建立您的應用程式的 Visual Studio 工具組版本。 Visual Studio 2017 和 Visual Studio 2015 有相容的工具組版本號碼，這表示可轉散發檔案可能會由使用 2015年工具組所建置的應用程式的 Visual Studio 2017。 雖然它們相容，我們不支援使用利用 2017年工具組所建置的應用程式中的 2015年可轉散發檔案。 我們只支援使用相同或比工具組版本還新的可轉散發套件。 如需最新支援可轉散發套件的舊版工具組的連結，請參閱[最新支援 Visual c + + 下載](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)。 可以藉由搜尋找到特定的較早版本的可轉散發套件[Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431)如 「 Visual c + + 可轉散發套件 」。

包含您的安裝程式的可轉散發 Dll 的另一種方式是使用*合併模組*。 這些 Microsoft Installer 模組中納入並安裝應用程式安裝程式。 在您的 Visual Studio 安裝目錄中找到可轉散發 Dll 的合併模組\\VC\\Redist\MSVC\\*版本*\\MergeModules\\. 在舊版的 Visual Studio 中，這些檔案位於您\\Program Files 或\\一般檔案中的 Program Files (x86) 目錄\\合併模組子目錄。 如需有關使用這些檔案，請參閱[使用合併模組轉散發的元件](../ide/redistributing-components-by-using-merge-modules.md)。

Visual Studio 的安裝中也包含個別的可轉散發 Dll。 根據預設，它們會安裝 Visual Studio 安裝目錄中\\VC\\可轉散發套件\\MSVC\\*版本*資料夾。 *版本*數字可能代表不同的次要組建數字的可轉散發檔案的單一通用集合。 使用最新任何的版本程式庫 DLL 檔案，可轉散發套件或在這些目錄中找到的合併模組。 您可以在您的應用程式的相同目錄中安裝這些，進行本機部署，使用這些程式庫。 我們不建議本機部署，因為它會讓您負責交給您已部署的應用程式的更新。 使用可轉散發套件集中部署時，最好。

若要判斷必須隨應用程式一起轉散發的 DLL，請收集應用程式所依賴的 DLL 並做成一份清單。 這些通常列在匯入程式庫連結器輸入。 某些程式庫，例如 vcruntime 和通用 C 執行階段程式庫 (UCRT)，包含預設值。 如果您的應用程式或其相依性的其中一個使用 LoadLibrary 以動態方式載入的 DLL，DLL 可能不會列在連結器輸入。 一種方式來收集動態載入的 Dll 清單為您的應用程式上執行 Dependency Walker (depends.exe) 中所述[了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 不幸的是，此工具已經過時，而且可能會回報，找不到某些 Dll。

當您有相依性的清單時，比較在 Microsoft Visual Studio 安裝目錄下找到該 Redist.txt 檔案的連結清單或 「 可轉散發清單 」 可轉散發 Dll 的 「 可散布程式碼檔案 > 一節中所參考Visual Studio 的 Microsoft 軟體授權條款。 Visual Studio 2017，請參閱[Microsoft Visual Studio 2017 （包括公用程式、 擴充性及 BuildServer 檔案） 的可散發程式碼](http://go.microsoft.com/fwlink/?LinkId=823098)。 Visual Studio 2015，請參閱[Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK （包含公用程式與 BuildServer 檔案） 的可散發程式碼](http://go.microsoft.com/fwlink/?LinkId=799794)。 Visual Studio 2013，清單位於線上[Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 可散發程式碼](http://go.microsoft.com/fwlink/p/?LinkId=313603)。

在 Visual Studio 2015 之前的 Visual Studio 版本，C 執行階段程式庫 (CRT) 並以可轉散發的 DLL，msvc 中包括*版本*.dll。 從 Visual Studio 2015 開始，CRT 中的函式已重構為 vcruntime 和 UCRT。 UCRT 現在是在 Windows 10 中，由 Windows Update 管理的系統元件。 所有 Windows 10 作業系統上使用。 若要部署到舊版作業系統的應用程式，您可能需要重新發佈 UCRT 也。 如果已不安裝任何版本的 UCRT，UCRT 的較早版本是包含在 Visual Studio 可轉散發檔案，只能安裝在作業系統早於 Windows 10，而且只。 以 Microsoft 系統更新封裝的形式為下層系統 UCRT 可安裝的版本，請參閱[Windows 10 通用 C 執行階段](https://www.microsoft.com/en-us/download/details.aspx?id=48234)在 Microsoft 下載中心取得。

並不是 Visual Studio 中包含的檔案都可讓您轉散發；您只能轉散發 Redist.txt 或線上「REDIST 清單」中指定的檔案。 您不能轉散發偵錯版本的應用程式以及各種 Visual C++ 偵錯 DLL。 如需詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。

下表描述您的應用程式可能依賴的部分 Visual C++ DLL。

|Visual C++ 程式庫|描述|適用於|
|--------------------------|-----------------|----------------|
|vcruntime*版本*.dll|原生程式碼的執行階段程式庫。|使用一般 C 和 c + + 語言啟動和終止服務的應用程式。|
|vccorlib*版本*.dll|Managed 程式碼的執行階段程式庫。|使用 managed 程式碼的 c + + 語言服務的應用程式。|
|msvcp*版本*.dll|原生程式碼針對 c + + 標準程式庫。|使用應用程式[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。|
|concrt*版本*.dll|並行執行階段程式庫，原生程式碼。|使用應用程式[並行執行階段](../parallel/concrt/concurrency-runtime.md)。|
|mfc*版本*.dll|Microsoft Foundation Class (MFC) 程式庫。|使用應用程式[MFC 程式庫](../mfc/mfc-desktop-applications.md)。|
|mfc*版本**語言*.dll|Microsoft Foundation Class (MFC) 程式庫資源。|Mfc 使用特定語言資源的應用程式。|
|mfc*版本*u.dll|具有 Unicode 支援的 MFC 程式庫。|使用應用程式[MFC 程式庫](../mfc/mfc-desktop-applications.md)並需要 Unicode 支援。|
|mfcmifc80.dll|MFC Managed 介面程式庫。|使用應用程式[MFC 程式庫](../mfc/mfc-desktop-applications.md)與[Windows Form 控制項](/dotnet/framework/winforms/controls/index)。|
|mfcm*版本*.dll|MFC Managed 程式庫。|使用應用程式[MFC 程式庫](../mfc/mfc-desktop-applications.md)與[Windows Form 控制項](/dotnet/framework/winforms/controls/index)。|
|mfcm*版本*u.dll|具有 Unicode 支援的 MFC Managed 程式庫。|使用應用程式[MFC 程式庫](../mfc/mfc-desktop-applications.md)與[Windows Form 控制項](/dotnet/framework/winforms/controls/index)並需要 Unicode 支援。|
|vcamp*版本*.dll|原生程式碼 AMP 程式庫。|使用應用程式[c + + AMP 程式庫](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)程式碼。|
|vcomp*版本*.dll|原生程式碼的 OpenMP 程式庫。|使用應用程式[c + + OpenMP 程式庫](../parallel/openmp/openmp-in-visual-cpp.md)程式碼。|

> [!NOTE]
> 您不再需要以個別 DLL 的形式轉散發 Active Template Library。 其功能已移至標頭和靜態程式庫。

如需如何轉散發這些 Dll，與您的應用程式的詳細資訊，請參閱[轉散發 Visual c + + 檔案](../ide/redistributing-visual-cpp-files.md)。 如需範例，請參閱[部署範例](../ide/deployment-examples.md)。

一般而言，您並不需要轉散發系統 Dll，因為它們是作業系統的一部分。 但是，還是有一些例外情形，例如當應用程式會在數個版本的 Microsoft 作業系統上執行時。 在此情況下，請務必閱讀對應的授權條款。 另外，請嘗試透過 Windows Update、Service Pack 或 Microsoft 提供的可轉散發套件，將系統 DLL 升級。

## <a name="see-also"></a>另請參閱

[選擇部署方法](../ide/choosing-a-deployment-method.md)

[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)

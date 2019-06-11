---
title: 在 Visual Studio 中使用原生多目標來建置舊專案
ms.date: 11/04/2016
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: 35f6ac980a451b375d5005c20853fdd29c78d96d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448949"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>在 Visual Studio 中使用原生多目標來建置舊專案

一般來說，建議您在安裝最新版 Visual Studio 時更新專案。 更新專案和程式碼的成本通常高於新 IDE、編譯器、程式庫和工具的優點。 不過，我們知道您可能無法更新某些專案。 您可能會有繫結至舊版程式庫或平台的二進位檔，但基於維護原因而無法進行升級。 您的程式碼可以使用非標準語言建構，而非標準語言建構會在您移至較新編譯器時中斷。 您的程式碼可能會依賴針對特定 Visual C++ 版本所編譯的協力廠商程式庫。 或者，您可能必須針對將目標設為特定舊版 Visual C++ 的其他版本產生程式庫。

幸運的是，您可以使用 Visual Studio 2017 和 Visual Studio 2015 來建置目標為舊版編譯器工具組和程式庫的專案。 您不需要升級 Visual Studio 2010、Visual Studio 2012、Visual Studio 2013 或 Visual Studio 2015 專案，即可利用 IDE 中的新功能：

  - 新的 C++ 重構功能和編輯器實驗性功能
  - 新的診斷工具偵錯工具視窗和錯誤清單視窗
  - 改寫的中斷點、例外狀況視窗和新的效能提示
  - 新的程式碼瀏覽和搜尋工具
  - 新的 C++ 快速修正和生產力支援工具延伸模組。

您也可以將目標設為 Visual Studio 2008 專案，但它們必須進行變更才能使用。 如需詳細資料，請參閱 **Visual Studio 2008 的指示**一節。

最新版 Visual Studio 支援專案的原生多目標和往返。 原生多目標是使用舊版 Visual Studio 所安裝的工具組來建置的最新 IDE 能力。 往返是最新 IDE 載入舊版 IDE 所建立的專案而不對專案進行任何變更的能力。 如果您並存安裝最新版 Visual Studio 與現有版本，則可以搭配使用新版 IDE 與現有版本的編譯器和工具來建置專案。 您小組的其他成員可以繼續在舊版 Visual Studio 中使用專案。

當您使用舊版工具組時，可以利用許多最新 IDE 功能，但不能利用 C++ 編譯器、程式庫和建置工具中的最先進功能。 例如，您無法使用新的語言一致性改善、新偵錯和程式碼分析功能，或取得最新工具組的更快速建置輸送量。 也會有一些 IDE 功能與舊版工具組不相容。 例如，記憶體分析工具中可能會遺失類型資訊，而且重構作業**轉換為原始字串常值**會產生當您使用 Visual Studio 2012 或舊版工具組時不會編譯之符合 C++11 標準的程式碼。

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>如何在 Visual Studio 中使用原生多目標

並存安裝 Visual Studio 與舊版本之後，請在新版 Visual Studio 中開啟現有專案。 載入專案時，Visual Studio 會詢問您是否要將它升級成使用最新的 C++ 編譯器和程式庫。 因為您想要專案保留舊版編譯器和程式庫，所以請選擇 [取消]  按鈕。

Visual Studio 一律會升級您的專案。 若要避免在每次載入專案時看到升級對話方塊，您可以在專案中或者其所匯入的 .props 或 .targets 檔案中定義下列屬性：

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

當您想要升級專案時，必須移除這個屬性。

如果您選擇不升級，則 Visual Studio 不會變更方案或專案檔。 當您建置專案時，產生的二進位檔會與您使用舊版 Visual Studio 所建置的二進位檔完全相容。 原因是 Visual Studio 會使用相同的 C++ 編譯器，並且連結舊版 IDE 隨附的相同程式庫。 這也是您選擇 [取消]  時，升級對話方塊警告您保留已安裝的舊版 Visual Studio 的原因。

## <a name="instructions-for-visual-studio-2008"></a>Visual Studio 2008 的指示

Visual Studio 2008 有自己適用於 C++ 的專屬建置系統，稱為 **VCBuild**。 從 Visual Studio 2010 開始，Visual Studio C++ 專案已變更成使用 **MSBuild**。 這表示您必須瀏覽在 Visual Studio 最新版本中建置 Visual Studio 2008 專案的更新步驟。 已更新的專案仍然會產生與使用 Visual Studio 2008 IDE 所建立的二進位檔完全相符的二進位檔。

首先，除了 Visual Studio 的目前版本之外，您還必須在與 Visual Studio 2008 相同的電腦上安裝 Visual Studio 2010。 只有 Visual Studio 2010 才會安裝將目標設為 Visual Studio 2008 專案所需的 **MSBuild** 指令碼。

接下來，您必須將 Visual Studio 2008 方案和專案更新成目前 Visual Studio 版本。 建議您在升級之前建立專案和方案檔的備份。 若要開始升級程序，請在目前 Visual Studio 版本中開啟方案。 當您收到升級提示時，請檢閱出現的資訊，然後選擇 [確定]  開始升級。 如果方案中有多個專案，則必須更新。這個精靈會建立與現有 .vcproj 檔案並存的新 .vcxproj 專案檔。 只要您同時擁有原始 .sln 檔案的複本，升級就不會對現有 Visual Studio 2008 專案造成其他影響。

升級完成時，如果記錄檔報表具有任何專案的錯誤或警告，則請仔細進行檢閱。 從 **VCBuild** 轉換成 **MSBuild** 可能會造成問題。 請確定您了解並實作報表中所列出的任何動作項目。 如需詳細資訊，以了解升級記錄報表以及將 **VCBuild** 轉換為 **MSBuild** 時可能發生的問題，請參閱這篇 [C++ Native Multi-Targeting](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) (C++ 原生多目標) 部落格文章。

如果完成專案升級，並且您已更正記錄檔中的任何問題，則方案會實際將目標設為最新工具組。 在最後一個步驟，將方案中每個專案的屬性都變更成使用 Visual Studio 2008 工具組。 在 Visual Studio 的目前版本中載入方案之後，針對方案中的每個專案，開啟專案的 [屬性頁]  對話方塊：以滑鼠右鍵按一下 [方案總管]  中的專案，然後選取 [屬性]  。 在 [屬性頁]  對話方塊中，將 [組態]  下拉式值變更為 [所有組態]  。 在 [組態屬性]  中，選取 [一般]  ，然後將 [平台工具組]  變更為 [Visual Studio 2008 (v90)]  。

在這項變更之後，當您在目前 Visual Studio 版本中建置方案時，會使用 Visual Studio 2008 編譯器和程式庫來產生專案二進位檔。

## <a name="install-an-older-visual-studio-toolset"></a>安裝舊版 Visual Studio 工具組

您可能有無法升級或不想要升級的舊 Visual Studio C++ 專案，但平台工具組版本與專案不符。 在此情況下，若要取得工具組，您可以安裝所需版本的免費 Visual Studio Community 或 Express 版本。 從 Visual Studio 2008 開始的每個 Visual Studio 版本，都可以安裝從目前 Visual Studio 將目標設為該版本所需的編譯器、工具和程式庫。 搜尋 Microsoft 下載中心以尋找並下載特定 Visual Studio 版本。 請確定您在安裝期間選擇 C++ 安裝選項。 安裝完成之後，請執行該 Visual Studio 版本來安裝任何更新。 同時檢查可能需要的任何 Windows Update 變更。 這項更新檢查程序可能需要重複進行多次，才能取得每個更新。

如需目前可用的下載，請參閱[下載舊版 Visual Studio 軟體](https://visualstudio.microsoft.com/vs/older-downloads/)。

安裝這些產品之後，[屬性頁]  對話方塊的 [平台工具組]  屬性下拉式清單會自動更新，以顯示可用的工具組。 您現在可以使用最新版的 Visual Studio 來建置適用於這些舊版工具組的專案，而不需要轉換或升級這些專案。

## <a name="see-also"></a>另請參閱

[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual Studio 中的 C++ 一致性改善](../overview/cpp-conformance-improvements.md)

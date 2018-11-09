---
title: 通用 CRT 部署
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 90f859eb0e9134c997e7eecad118cfb8ec00b782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657687"
---
# <a name="universal-crt-deployment"></a>通用 CRT 部署

從 Visual Studio .NET 到 Visual Studio 2013，C++ 編譯器和工具的每個主要版本都包含 Microsoft C 執行階段 (CRT) 程式庫的新獨立版本。 這些 CRT 獨立版本彼此無關，且在不同程度上互不相容。 例如，Visual Studio 2012 所使用的 CRT 程式庫是第 11 版，名為 msvcr110.dll，而 Visual Studio 2013 所使用的 CRT 是第 12 版，名為 msvcr120.dll。 從 Visual Studio 2015 開始，就不再是這種情況。 Visual Studio 2015 和更新版本的 Visual Studio 全都使用一個通用 CRT。

通用 CRT 是 Microsoft Windows 作業系統的元件。 它在 Windows 10 已包含作為作業系統的一部分，而在 Windows Vista 到 Windows 8.1 的較舊作業系統中則可透過 Windows Update 取得。 此外，還支援本機部署通用 CRT，但有一些限制。

## <a name="central-deployment"></a>集中部署

集中安裝通用 CRT 的慣用方法是使用 Microsoft Windows Update。 通用 CRT 是所有支援的 Microsoft Windows 作業系統的建議更新 ；因此根據預設，大部分的電腦都會在定期更新程序期間安裝它。 通用 CRT 的初始版本是 [KB2999226](https://support.microsoft.com/kb/2999226)；在 [KB3118401](https://support.microsoft.com/kb/3118401) 進行了包含各種 Bug 修正的後續更新，而且還有包含其他 Bug 修正和新功能的其他更新。 如需較新的更新，請在 [support.microsoft.com](https://support.microsoft.com) 中搜尋通用 C 執行階段或通用 CRT。

並非所有的 Microsoft Windows 電腦都會使用 Windows Update 定期安裝更新，而且某些電腦可能不會安裝所有建議的更新。 為了支援使用透過 Visual Studio 2015 和更新版本的 C++ 工具組在這些機器上所建置的應用程式，有適用於離線散發的通用 CRT 可轉散發套件。 這些可轉散發套件可以從上述其中一個 KB 連結下載。 請注意，通用 CRT 可轉散發套件需要電腦已更新為最新的 Service Pack。 因此，比方說，Windows 7 的可轉散發套件只能安裝到 Windows 7 SP1，而不是 Windows 7 RTM。

由於通用 CRT 是 C++ 程式庫的基本相依性，因此 Visual C++ 可轉散發套件 (VCRedist) 會在未安裝某個版本的電腦上安裝通用 CRT 的基底版本，這足以滿足 C++ 程式庫版相依性。 如果應用程式相依於較新版本的通用 CRT，您必須明確地安裝該較新版本。 最好在安裝 VCRedist 之前先安裝此版本，以避免發生可能的多次必要重新開機。

## <a name="local-deployment"></a>本機部署

支援本機部署通用 CRT，但基於效能和安全性原因不建議使用。  本機部署的 DLL 是包含作為 Windows SDK 的一部分，依電腦架構位於 Windows Kits\\10\\Redist\\ucrt\\DLLs 子目錄中。 所需的 DLL 包括 ucrtbase.dll 和一組名為 api-ms-win-\*.dll 的 APISet 轉寄站 DLL。 每個作業系統上所需的這組 DLL 都不同，因此強烈建議您在本機部署時包括所有的 DLL。

本機部署有兩項要注意的限制：

- 在 Windows 10 上，即使應用程式包含通用 CRT 的應用程式本機複本，也一律會使用系統目錄中的通用 CRT。 即使通用 CRT 的本機複本是較新版本，也是如此。 這是因為通用 CRT 是 Windows 10 上的核心作業系統元件。

- 在 Windows 8 之前的 Windows 版本中，通用 CRT 無法使用包含應用程式主要可執行檔的目錄以外的目錄中所含的外掛程式，在本機進行封裝。 在此情況下，APISet 轉寄站 DLL 無法成功解析 ucrtbase.dll。 一些建議的替代解決方案包括：

  - 以靜態方式連結通用 CRT，
  - 集中部署通用 CRT，或
  - 將通用 CRT 檔案放在與應用程式相同的目錄中。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP 上的部署

Visual Studio 2015 和 Visual Studio 2017 持續支援開發用於 Microsoft Windows XP 的軟體。 為了支援此作業，通用 CRT 的版本可在 Microsoft Windows XP 上運作。 Microsoft Windows XP 作業系統已不再位於主流或延伸支援中，因此將通用 CRT 集中部署到 Microsoft Windows XP 的作業不同於其他作業系統。

在 Windows XP 上安裝 Visual C++ 可轉散發套件時，它會直接將通用 CRT 及其所有相依性安裝到系統目錄中，而不需要安裝或依據任何 Windows Update。 可轉散發合併模組 (Microsoft_VC*version*_CRT_\*.msm 檔案) 會執行相同的處理。

在 Windows XP 上本機部署通用 CRT 的作業與其他支援作業系統上的相同。

## <a name="see-also"></a>另請參閱

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)

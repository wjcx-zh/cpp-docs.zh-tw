---
title: Universal CRT 部署 |Microsoft 文件
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="universal-crt-deployment"></a>Universal CRT 的部署

透過 Visual Studio 2013 Visual Studio.NET 中，從 c + + 編譯器和工具的每個主要版本包含了新的獨立版本的 Microsoft C 執行階段 (CRT) 程式庫。 CRT 這些獨立版本是獨立的以及各種程度互不相容。 比方說，Visual Studio 2012 所使用的 CRT 程式庫版本 11，具名的 msvcr110.dll，並使用 Visual Studio 2013 CRT 已版本 12、 具名的 msvcr120.dll。 從 Visual Studio 2015 開始，這是不再大小寫。 Visual Studio 2015 和更新版本的 Visual Studio 的所有使用一個通用的 CRT。

Universal CRT 是 Microsoft Windows 作業系統元件。 它是在 Windows 10 作業系統的一部分，可用於較舊的作業系統，透過 Windows 8.1 的 Windows Vista 使用 Windows Update。 此外，本機部署通用 CRT 的支援，但有一些限制。

## <a name="central-deployment"></a>集中部署

集中安裝通用 CRT 的慣用的方法是使用 Microsoft Windows Update。 Universal CRT 是所有建議的更新支援 Microsoft Windows 作業系統，因此預設，大部分的機器安裝定期更新程序的一部分。 Universal CRT 的初始版本[KB2999226](https://support.microsoft.com/en-us/kb/2999226); 具有各種 bug 修正的後續更新中已提出[KB3118401](https://support.microsoft.com/en-us/kb/3118401)，且已與其他 bug 修正和新功能的其他更新。 較新的更新，搜尋[support.microsoft.com](https://support.microsoft.com)通用 C 執行階段或通用 CRT。

並非所有的 Microsoft Windows 電腦定期使用 Windows Update 安裝更新和某些可能不會安裝所有建議的更新。 若要支援使用這些機器上使用 Visual Studio 2015 和更新版本的 c + + 工具組所建置的應用程式，有通用的 CRT 可轉散發套件適用於離線發佈。 可能從上述的 KB 連結下載這些的可轉散發套件。 請注意： 通用 CRT 可轉散發套件需要，電腦已更新為目前的 service pack。 因此，比方說，可轉散發套件適用於 Windows 7 只會安裝到 Windows 7 SP1、 未 Windows 7 RTM。

Visual c + + 可轉散發套件 (VCRedist) 通用的 CRT 是基本的 c + + 程式庫相依性，因為安裝不是已安裝，不足以滿足 c + + 程式庫版本的電腦上通用的 CRT 的基底版本相依性。 如果您的應用程式相依於較新版本的通用的 CRT，您必須明確地安裝該較新版本。 所以最好先安裝，才能安裝 VCRedist，以避免潛在的多個需要重新開機。

## <a name="local-deployment"></a>本機部署

Universal CRT 的本機部署受支援，但不是建議用於效能和安全性的理由。  本機部署的 Dll 是包含在 Windows SDK，在 Windows 套件\\10\\可轉散發套件\\ucrt\\Dll 子目錄，依電腦架構。 包含 ucrtbase.dll 與 APISet 轉寄站名為應用程式開發介面的 Dll 的一組 Dll 所需的 ms-win-\*.dll。 在各作業系統所需的 Dll 集合而有所不同，因此強烈建議您包含的所有 Dll 部署在本機上時。

有兩個要注意的本機部署的限制：

- 在 Windows 10 上系統目錄中： 通用 CRT 一律會使用，即使應用程式包含通用的 CRT 應用程式的本機副本。 即使是較新的通用 CRT 的本機複本，也是如此。 這是因為通用的 CRT 在 Windows 10 上的核心作業系統元件。

- 上的 Windows 8 之前的 Windows 版本中，通用 CRT 無法封裝在本機使用位於包含您的應用程式的主要可執行檔的目錄以外的目錄中的外掛程式。 APISet 轉寄站 Dll 將無法在此情況下成功解決 ucrtbase.dll。 某些建議的替代方案包括：

  - 以靜態方式連結通用的 CRT，
  - 集中部署通用的 CRT，或
  - Universal CRT 將檔案放在與應用程式相同的目錄。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP 上的部署

Visual Studio 2015 和 Visual Studio 2017 繼續支援 Microsoft Windows XP 上使用的軟體開發。 若要支援此作業，通用的 CRT 版本上運作 Microsoft Windows XP。 在 Microsoft Windows XP 作業系統已不存在於主要或延伸支援中，因此集中部署到 Microsoft Windows XP 上的通用 crt 是不同於其他作業系統。

在 Windows XP 上安裝 Visual c + + 可轉散發套件時，它直接安裝通用 CRT 和及其所有相依性到系統目錄中，而不需要安裝或根據任何 Windows Update。 可轉散發合併模組，Microsoft_VC*版本*_CRT_\*.msm 檔案執行相同的動作。

通用的 CRT，在 Windows XP 上的本機部署為其他支援的作業系統上的一樣。

## <a name="see-also"></a>另請參閱

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)

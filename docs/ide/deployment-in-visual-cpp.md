---
title: Visual C++ 中的部署
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 7ca65acef2395bca370aba9b6e435d3f3a152148
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568458"
---
# <a name="deployment-in-visual-c"></a>Visual C++ 中的部署

在開發電腦以外的電腦上安裝應用程式稱為「部署」。 在另一部電腦上部署 Visual C++ 應用程式時，您必須安裝該應用程式及該應用程式相依的所有程式庫檔案。 Visual Studio 可透過三種方法在您部署應用程式時一併部署 Visual C++ 程式庫：「集中部署」、「本機部署」或「靜態連結」。 集中部署會將程式庫檔案放置在 Windows 目錄下，Windows Update 服務就可以自動更新這些檔案。 本機部署會將程式庫檔案放置在與應用程式相同的目錄中。 您必須自行重新部署任何本機部署的程式庫，才能更新它們。 靜態連結會將程式庫程式碼繫結到應用程式。 當您使用靜態連結時，必須重新編譯並重新部署應用程式，才能利用程式庫的任何更新。

在 Visual Studio 2015 中，Microsoft C 執行階段程式庫已重構為特定版本的本機程式庫元件，以及現在是 Windows 一部分的新通用 C 執行階段程式庫。 如需通用 CRT 部署的詳細資料，請參閱[通用 CRT 部署](universal-crt-deployment.md)。

## <a name="central-deployment"></a>集中部署

集中部署會將程式庫 DLL 檔案安裝在 Windows\System32 目錄中，如果是 x64 系統上的 32 位元程式庫檔案，則會安裝在 Windows\SysWow64 目錄中。 Microsoft 會自動更新集中部署的程式庫。 若是屬於本機部署或靜態連結的 Visual C++ 程式庫，您必須提供更新。

若要集中部署 Visual C++ 程式庫，您可以使用兩個來源檔的其中一個進行安裝：

- 「可轉散發套件檔」，這些是獨立的命令列可執行檔，其中包含壓縮格式的所有 Visual C++ 可轉散發程式庫，或

- 「可轉散發合併模組 (.msm 檔案)」，您可以用於部署特定程式庫，以及包含在應用程式 Windows Installer (.msi) 檔案中的程式庫。

可轉散發套件檔會安裝特定系統架構的所有 Visual C++ 程式庫。 例如，如果應用程式是針對 x64 所建置，您可以使用 vcredist_x64.exe 可轉散發套件來安裝應用程式所使用的所有 Visual C++ 程式庫。 在安裝應用程式之前，您可以設計應用程式安裝程式，將執行可轉散發套件設定為必要條件。

合併模組可以包含 Windows Installer 應用程式安裝檔中特定 Visual C++ 程式庫的安裝邏輯。 您可以包含應用程式所需數量的合併模組。 當您需要將部署二進位檔案的大小降到最低時，請使用合併模組。

由於藉由使用可轉散發套件進行集中部署，或者合併模組可讓 Windows Update 自動更新 Visual C++ 程式庫，建議您在應用程式中使用程式庫 DLL 而不是靜態程式庫，並使用集中部署而不是本機部署。

## <a name="local-deployment"></a>本機部署

本機部署會將程式庫檔案和可執行檔一同安裝在應用程式資料夾中。 因為每個版本的檔案名稱會包含其版本號碼，因此可以將不同版本的 Visual C++ 可轉散發程式庫安裝在相同資料夾中。 例如，第 12 版的 C++ 執行階段程式庫是 msvcp120.dll，而第 14 版是 msvcp140.dll。

程式庫可以分散在多個其他的 DLL 中，稱為「dot 文件庫」。 例如，Visual Studio 2017 15.6 版中發行的標準程式庫的某些功能已新增到 msvcp140_1.dll，用來維持 msvcp140.dll 的 ABI 相容性。 如果使用 Visual Studio 2017 15.6 版 (工具組 14.13) 或 Visual Studio 2017 中更新版本的工具組，您可能需要在本機部署這些 dot 程式庫，以及主要程式庫。 當 ABI 變更時，這些個別的 dot 程式庫就會轉入基底程式庫的下一個主要版本。

由於 Microsoft 無法自動更新本機部署的 Visual C++ 程式庫，建議您不要本機部署這些程式庫。 如果您決定使用可轉散發程式庫的本機部署，建議您自行實作能夠自動更新本機部署程式庫的方法。

## <a name="static-linking"></a>靜態連結

除了動態連結的程式庫，Visual Studio 還會提供其大部分的程式庫作為靜態程式庫。 您可以用靜態方式將靜態程式庫連結至應用程式，也就是說，將程式庫物件程式碼直接連結到應用程式。 這會建立沒有 DLL 相依性的單一二進位檔案，如此您便不需要分別部署 Visual C++ 程式庫檔案。 不過，由於無法就地更新靜態連結的程式庫，因此建議您不要採用這種方法。 如果您使用靜態連結而想要更新連結的程式庫，您必須重新編譯並重新部署應用程式。

## <a name="troubleshooting-deployment-issues"></a>針對部署問題進行移難排解

Visual C++ 程式庫的載入順序與系統相關。 若要診斷載入器問題，請使用 depends.exe 或 where.exe。 如需詳細資訊，請參閱[動態連結程式庫搜尋順序 (Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order)。

## <a name="see-also"></a>另請參閱

- [部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [通用 CRT 部署](universal-crt-deployment.md)

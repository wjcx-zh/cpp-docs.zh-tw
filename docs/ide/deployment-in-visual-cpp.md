---
title: "部署 Visual c + + |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2018
ms.technology:
- cpp-ide
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2356e98e911978dcaef9471f2b474c2a2377716d
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="deployment-in-visual-c"></a>Visual C++ 中的部署

您的開發電腦以外的電腦上的應用程式的安裝稱為*部署*。 當您部署至另一部電腦的 Visual c + + 應用程式時，您必須安裝應用程式與它相依於任何程式庫檔案。 Visual Studio 可讓部署應用程式一起 Visual c + + 程式庫的三種方式：*集中部署*，*本機部署*，和*靜態連結*。 集中部署會將 Windows 目錄下的程式庫檔案所在的 Windows Update 服務可以自動更新。 本機部署會將程式庫檔案放在與您的應用程式相同的目錄中。 您必須重新部署任何本機部署程式庫自行加以更新。 靜態連結會繫結到您的應用程式程式庫程式碼。 您必須重新編譯和重新部署您的應用程式的任何更新程式庫時利用您使用靜態連結。

## <a name="central-deployment"></a>集中部署

集中部署，在程式庫 DLL 檔案會安裝在 Windows\System32 目錄中，或在 x64 上的 32 位元程式庫檔案系統，Windows\SysWow64 目錄。 Microsoft 會自動更新集中部署的程式庫。 Visual c + + 程式庫，屬於本機部署或以靜態方式連結，您必須提供更新。

若要集中部署 Visual c + + 程式庫，您可以使用其中一個兩個來源檔案安裝：

- *可轉散發套件*檔案是獨立命令列可執行檔，包含所有的 Visual c + + 可轉散發程式庫是以壓縮格式，或

- *可轉散發合併模組*（.msm 檔案），您可以使用來部署特定程式庫，以及包含在應用程式的 Windows Installer (.msi) 檔案中。

可轉散發套件檔案會安裝所有 Visual c + + 程式庫，針對特定的系統架構。 例如，如果您的應用程式針對 x64 所建置，您可以使用 vcredist_x64.exe 可轉散發套件安裝應用程式所使用的所有 Visual c + + 程式庫。 您可以設計您的應用程式安裝程式執行可轉散發套件做為必要條件，才能安裝應用程式。

合併模組可以包含的 Windows Installer 應用程式安裝檔中的特定 Visual c + + 程式庫的安裝邏輯。 您可以包含應用程式需要較多或較少的合併模組。 當您需要部署二進位編碼檔案大小降到最低，請使用合併模組。

由於使用可轉散發套件 」 或 「 合併模組進行集中部署可讓 Windows Update 自動更新的 Visual c + + 程式庫，我們建議您在您的應用程式，而不是靜態程式庫中使用程式庫 Dll，並使用中央而不是本機部署的部署。

## <a name="local-deployment"></a>本機部署

在本機部署程式庫檔案會安裝在您的應用程式資料夾，以及可執行檔。 不同版本的 Visual c + + 可轉散發程式庫可以安裝在相同的資料夾，因為每個版本的檔案名稱包含其版本號碼。 例如，c + + 執行階段程式庫第 12 版也 msvcp120.dll，版本 14 msvcp140.dll。

程式庫可能分散在多個其他的 Dll，又稱為*點文件庫*。 比方說，在 Visual Studio 2017 版本 15.6 中發行的標準程式庫中的某些功能已加入到 msvcp140_1.dll，preverve msvcp140.dll 的 ABI 相容性。 如果您使用 Visual Studio 2017 版本 15.6 （工具組 14.13） 或更新版本的工具組，從 Visual Studio 2017，您可能需要在本機部署這些點程式庫，以及主要程式庫。 ABI 變更時，這些點個別文件庫接著復原基底文件庫的下一個主要版本。

由於 Microsoft 無法自動更新本機部署 Visual c + + 程式庫，我們不建議本機部署這些程式庫。 如果您決定使用可轉散發程式庫的本機部署，建議您自行實作能夠自動更新本機部署程式庫的方法。

## <a name="static-linking"></a>靜態連結

除了動態連結程式庫，Visual Studio 會提供大部分的程式庫為靜態程式庫。 以靜態方式，您可以也就是連結到您的應用程式的靜態程式庫、 程式庫物件程式碼直接連結到應用程式。 這會建立單一的二進位檔，而不 DLL 相依，如此您不需要分別部署 Visual c + + 程式庫檔案。 不過，我們不建議這種方法因為無法就地更新靜態連結程式庫。 如果您使用靜態連結而想要更新連結的程式庫，您必須重新編譯並重新部署應用程式。

## <a name="troubleshooting-deployment-issues"></a>移難排解部署問題

Visual c + + 程式庫的載入順序是系統而定。 若要診斷載入器問題，請使用 depends.exe 或 where.exe。 如需詳細資訊，請參閱[動態連結程式庫搜尋順序 (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)。

## <a name="see-also"></a>另請參閱

[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)
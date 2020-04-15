---
title: 選擇部署方法
ms.date: 03/14/2019
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
ms.openlocfilehash: 633b76458fdc24ef9ba551d8209c5c99720df37e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377398"
---
# <a name="choosing-a-deployment-method"></a>選擇部署方法

除非您的 Visual C++ 應用程式是獨立的，而且可以利用複製命令進行部署，否則建議您使用 Windows Installer 進行部署。 Windows Installer 支援安裝、修復或解除安裝，同時也支援不可部分完成更新應用程式檔案、相依性和登錄項目。

> [!NOTE]
> 雖然可以在 Visual Studio 中利用 [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) 方法部署 Visual C++ 原生應用程式，但必須執行額外的步驟。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md)。

## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++ 程式庫是共用 DLL

由於 Visual Studio 安裝程式會將 Visual C++ 程式庫安裝在 %windir%\system32\ 目錄中，當您開發與這些程式庫相依的 Visual C++ 應用程式時，該應用程式會如預期執行。 不過，若要在可能沒有安裝 Visual Studio 的電腦上部署該應用程式，建議您先確定已將程式庫和應用程式一併安裝在那些電腦中。

## <a name="redistributing-visual-c-libraries"></a>轉散發 Visual C++ 程式庫

在您的部署中，您可以轉散發具有轉散發授權的任何 Visual C++ 程式庫版本。 部署方法有三種：

- 使用可轉散發套件集中部署，這會將 Visual C++ 程式庫安裝在 %windir%\system32\\ 中作為共用的 DLL (在此資料夾中安裝需要管理員許可權。在目標電腦上安裝應用程式之前,您可以建立執行可再分發包的文稿或安裝程式。 可轉散發套件適用於 x86、x64 和 ARM 平台 (VCRedist_x86.exe、VCRedist_x64.exe 或 VCRedist_arm.exe)。 Visual Studio 將這些套件包含在 %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\ 中。 您也可以從 [Microsoft 下載中心](https://www.microsoft.com/download)下載檔案 (使用下載中心的搜尋方塊，搜尋與您的應用程式相符的「Visual C++ 可轉散發套件 <Visual Studio 版本及更新>**」。 例如,如果您使用 Visual Studio 2015 更新 3 來構建應用程式,則搜索"可視C++可再分發包 2015 更新 3"。有關如何使用可再分發包的資訊,請參閱[演練:透過使用可視C++可再分發包部署可視C++應用程式](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。

- 使用合併模組進行集中部署時，每一個模組各會將一個特定的 Visual C++ 程式庫安裝在 %windir%\system32\\ 中作為共用的 DLL (安裝到此資料夾需要管理員許可權。合併模組將成為應用程式的 .msi 安裝程式檔的一部分。 Visual C++ 可轉散發合併模組包含在 Visual Studio 的 \Program Files (x86)\Common Files\Merge Modules\\ 中。 如需詳細資訊，請參閱[使用合併模組轉散發](redistributing-components-by-using-merge-modules.md)。

- 本機部署，使用此方法時，您可以從 Visual Studio 安裝複製特定的 Visual C++ DLL (通常位於 \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\)，再將這些 DLL 安裝在目標電腦上應用程式可執行檔所在的相同資料夾中。 您可以使用此部署方法讓不具系統管理員權限的使用者進行安裝，也可以用於安裝可透過網路共用執行的應用程式。

若部署使用可轉散發合併模組，但由不具系統管理權限的使用者執行安裝，則不會安裝 Visual C++ DLL，應用程式也不會執行。 此外，以合併模組建置 (允許個別使用者安裝) 的應用程式安裝程式會將程式庫安裝在共用位置，此位置會影響系統的所有使用者。 您可以使用本機部署將必要的 Visual C++ DLL 安裝在特定使用者的應用程式目錄中，而不會影響其他使用者，也不需要具備系統管理員權限。 由於這可能會產生服務性問題，因此我們不建議本機部署 Visual C++ 可轉散發 DLL。

不正確的 Visual C++ 程式庫部署方式可能會在執行相依的應用程式時發生執行階段錯誤。 當操作系統載入應用程式時,它使用[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中描述的搜尋順序。

## <a name="dynamic-linking-is-better-than-static-linking"></a>動態連結比靜態連結適合

建議您避免轉散發 Visual C++ 程式庫時使用靜態連結。 靜態連結幾乎無法大幅改善應用程式效能，卻會提高服務代價。 例如，請考慮靜態連結至已更新安全性增強之程式庫的應用程式，除非重新編譯並重新部署，否則該應用程式不會因此受益。 相反地，我們建議您將應用程式動態連結至相依的程式庫，以便在部署時更新這些程式庫。

## <a name="see-also"></a>另請參閱

[部署桌面應用程式](deploying-native-desktop-applications-visual-cpp.md)<br>
[單擊"一次安全和部署"](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[部署範例](deployment-examples.md)

---
title: Visual C++ 應用程式的 ClickOnce 部署
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 83ee85dbf952fd78a1cd1b8d0c932b9dcd02682d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407077"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Visual C++ 應用程式的 ClickOnce 部署

Visual Studio 提供兩種不同的技術來部署 Windows 應用程式：ClickOnce 部署或 [Windows Installer](/windows/desktop/Msi/windows-installer-portal) 部署。

## <a name="clickonce-deployment-in-c"></a>C++ 中的 ClickOnce 部署

Visual C++ 開發環境不直接支援使用 ClickOnce 部署 Visual C++ 專案，但是有提供工具可使用它。

> [!NOTE]
>  Visual Studio 在 Visual C# 和 Visual Basic 開發環境中支援 ClickOnce。 如果 Visual C++ 專案是 Visual C# 專案的相依性，您就可以從 Visual C# 開發環境使用 ClickOnce 部署來發佈應用程式 (包括它的相依性)。

若要使用 ClickOnce 部署 Visual c + + 應用程式，您必須先使用 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) 或它的圖形化使用者介面版本 (如需資訊，請參閱[MageUI.exe (資訊清單產生和編輯工具、圖形化用戶端)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client))，建置 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)和 [ClickOnce 部署資訊清單](/visualstudio/deployment/clickonce-deployment-manifest)。

請先使用 Mage.exe 建置應用程式資訊清單，產生的檔案會有 .manifest 的副檔名。 接著，使用 Mage.exe 建置部署資訊清單，而產生的檔案會有 .application 的副檔名。 然後，簽名資訊清單。

應用程式資訊清單必須指定目標處理器 (**x86**、**x64** 或 **ARM**)。 請參閱 [64 位元應用程式的部署必要條件](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)，以取得這些選項的詳細資訊。

此外，應用程式和部署資訊清單的名稱必須與 C++ 應用程式的名稱不同。 這可避免 Mage.exe 所建立的應用程式資訊清單，與屬於 C++ 應用程式一部分的外部資訊清單發生衝突。

您的部署將需要安裝應用程式所依賴的任何 Visual C++ 程式庫。 若要判斷特定應用程式的相依性，您可以搭配 /DEPENDENTS 選項使用 depends.exe 或 DUMPBIN 公用程式。 如需相依性的詳細資訊，請參閱[了解 Visual C++ 應用程式的相依性](understanding-the-dependencies-of-a-visual-cpp-application.md)。 您可能必須執行 VCRedist.exe，這個公用程式會在目標電腦中安裝 Visual C++ 程式庫。

此外，您可能還需要為應用程式建置啟動載入器 (Bootstrapper) (必要條件安裝程式) 來部署必要條件元件。如需啟動載入器的詳細資訊，請參閱[建立啟動載入器套件](/visualstudio/deployment/creating-bootstrapper-packages)。

如需這項技術的詳細描述，請參閱 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 如需 ClickOnce 部署的詳細範例，請參閱[逐步解說：手動部署 ClickOnce 應用程式](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)。

## <a name="see-also"></a>另請參閱

[Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert.exe (憑證建立工具)](https://msdn.microsoft.com/library/windows/desktop/aa386968)<br>
[部署傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)<br>
[部署應用程式、服務和元件](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[建立啟動載入器套件](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

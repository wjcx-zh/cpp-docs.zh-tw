---
title: Visual c + + 應用程式的 ClickOnce 部署 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e85ec0dfc011aab4d2b3ac835bbe71782b055000
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Visual C++ 應用程式的 ClickOnce 部署
Visual Studio 部署 Windows 應用程式提供兩種不同技術： ClickOnce 部署或[Windows Installer](http://msdn.microsoft.com/library/cc185688)部署。  
  
## <a name="clickonce-deployment-in-c"></a>C++ 中的 ClickOnce 部署  
 Visual c + + 開發環境不直接支援的 Visual c + + 專案，使用 ClickOnce 部署，但工具就可以使用它。  
  
> [!NOTE]
>  Visual Studio 的 Visual C# 和 Visual Basic 開發環境中支援 ClickOnce。 如果您的 Visual c + + 專案的 Visual C# 專案相依性，您可以發行應用程式 （包括其相依性） 使用 ClickOnce 部署從 Visual C# 開發環境。  
  
 若要部署使用 ClickOnce 的 Visual c + + 應用程式，您必須先建置[ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)和[ClickOnce 部署資訊清單](/visualstudio/deployment/clickonce-deployment-manifest)使用[Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)或它的圖形化使用者介面版本 (資訊，請參閱[MageUI.exe （資訊清單產生和編輯工具、 圖形化用戶端）](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client))。  

  
 請先使用 Mage.exe 建置應用程式資訊清單，產生的檔案會有 .manifest 的副檔名。 接著，使用 Mage.exe 建置部署資訊清單，而產生的檔案會有 .application 的副檔名。 然後，簽名資訊清單。  
  
 應用程式資訊清單必須指定目標處理器 (**x86**， **x64**，或**ARM**)。 請參閱[64 位元應用程式的部署必要條件](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)有關這些選項的資訊。  
  
 此外，應用程式和部署資訊清單的名稱必須與 C++ 應用程式的名稱不同。 這可避免 Mage.exe 所建立的應用程式資訊清單，與屬於 C++ 應用程式一部分的外部資訊清單發生衝突。  
  
 您的部署將需要安裝您的應用程式所依賴的任何 Visual c + + 程式庫。 若要判斷特定應用程式的相依性，您可以搭配 /DEPENDENTS 選項使用 depends.exe 或 DUMPBIN 公用程式。 如需有關相依性的詳細資訊，請參閱[了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。 您可能需要執行 VCRedist.exe;此公用程式會在目標電腦上安裝 Visual c + + 程式庫。  
  
 您可能也需要為您的應用程式部署必要條件的元件; 建置啟動載入器 （必要條件安裝程式）如需啟動載入器資訊，請參閱[建立啟動載入器套件](/visualstudio/deployment/creating-bootstrapper-packages)。  
  
 如需更詳細的技術說明，請參閱[ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)。 ClickOnce 部署的詳細範例，請參閱[逐步解說： 手動部署 ClickOnce 應用程式](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)。  
  
## <a name="see-also"></a>另請參閱  
 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Makecert.exe (憑證建立工具)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [部署應用程式、 服務和元件](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Windows Installer 部署](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)   
 [建立啟動載入器套件](/visualstudio/deployment/creating-bootstrapper-packages)   
 [.NET 程式設計使用 C + + /CLI （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
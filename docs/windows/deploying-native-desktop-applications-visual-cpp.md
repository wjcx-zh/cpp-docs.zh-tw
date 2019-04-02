---
title: 部署原生桌面應用程式 (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.openlocfilehash: 46ced4ac5f7952a9b7f66418ea037e053b16e9be
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786172"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>部署原生桌面應用程式 (Visual C++)

部署是指用來散發已完成的應用程式或元件，以便在其他電腦上進行安裝的程序。 當應用程式在開發人員的電腦上完成建立時，即開始部署規劃。 當應用程式已安裝並準備在使用者的電腦上執行時，即結束部署。

Visual Studio 提供各種不同的技術來部署 Windows 應用程式。 這些技術包括 ClickOnce 部署和 Windows Installer 部署。

- ClickOnce 可用來部署以 Common Language Runtime (CLR) 為目標的 C++ 應用程式，CLR 是混合、純粹且和可驗證的組件。 雖然您可以使用 Windows Installer 來部署受控應用程式，但建議您使用 ClickOnce 以利用 .NET Framework 安全性功能，例如資訊清單簽署。 ClickOnce 不支援原生 C++ 應用程式的部署。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](clickonce-deployment-for-visual-cpp-applications.md)。

- Windows Installer 技術可用來部署原生 C++ 應用程式或以 CLR 為目標的 C++ 應用程式。

本文下一節所提供的文章，討論如何確保原生 Visual C++ 應用程式在提供支援之目標平台的任何電腦上執行；您必須在安裝套件中包含哪些檔案；以及轉散發應用程式相依元件的建議做法。

## <a name="in-this-section"></a>本節內容

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)

- [部署概念](deployment-concepts.md)

- [了解 Visual C++ 應用程式的相依性](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [決定要轉散發哪些 DLL](determining-which-dlls-to-redistribute.md)

- [選擇部署方法](choosing-a-deployment-method.md)

- [通用 CRT 部署](universal-crt-deployment.md)。

- [轉散發 Visual C++ 檔案](redistributing-visual-cpp-files.md)

- [部署範例](deployment-examples.md)

- [轉散發 Web 用戶端應用程式](redistributing-web-client-applications.md)

- [Visual C++ 應用程式的 ClickOnce 部署](clickonce-deployment-for-visual-cpp-applications.md)

- [在舊版執行階段版本上執行 C++ /clr 應用程式](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>相關章節

- [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [部署](/dotnet/framework/deployment/index)

- [疑難排解 C/C++ 隔離應用程式和並存組件](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
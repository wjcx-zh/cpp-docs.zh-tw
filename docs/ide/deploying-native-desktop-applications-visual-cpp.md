---
title: 部署原生桌面應用程式 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f4aa355c132b4c94f085cbdf7aa73785357d0f0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="deploying-native-desktop-applications-visual-c"></a>部署原生桌面應用程式 (Visual C++)

部署是指用來散發已完成的應用程式或元件，以便在其他電腦上進行安裝的程序。 當應用程式在開發人員的電腦上完成建立時，即開始部署規劃。 當應用程式已安裝並準備在使用者的電腦上執行時，即結束部署。

Visual Studio 提供各種不同的技術來部署 Windows 應用程式。 這些包括 ClickOnce 部署和 Windows Installer 部署。

- ClickOnce 可以用來部署以 common language runtime (CLR) 為目標的 c + + 應用程式 — 混合的、 純粹的和可驗證的組件。 雖然您可以使用 Windows Installer 來部署 managed 應用程式，我們建議您使用 ClickOnce，因為它會利用.NET Framework 安全性功能，例如資訊清單簽署。 ClickOnce 不支援原生 c + + 應用程式的部署。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。

- Windows Installer 技術可用來部署原生 C++ 應用程式或以 CLR 為目標的 C++ 應用程式。

本文下一節所提供的文章，討論如何確保原生 Visual C++ 應用程式在提供支援之目標平台的任何電腦上執行；您必須在安裝套件中包含哪些檔案；以及轉散發應用程式相依元件的建議做法。

## <a name="in-this-section"></a>本節內容

- [Visual C++ 中的部署](../ide/deployment-in-visual-cpp.md)

- [部署概念](../ide/deployment-concepts.md)

- [了解 Visual C++ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

- [決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md)

- [選擇部署方法](../ide/choosing-a-deployment-method.md)

- [Universal CRT 部署](universal-crt-deployment.md)。

- [轉散發 Visual C++ 檔案](../ide/redistributing-visual-cpp-files.md)

- [部署範例](../ide/deployment-examples.md)

- [轉散發 Web 用戶端應用程式](../ide/redistributing-web-client-applications.md)

- [Visual C++ 應用程式的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)

- [在舊版的執行階段版本上執行 c + + /clr 應用程式](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>相關章節

- [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [部署](/dotnet/framework/deployment/index)

- [疑難排解 C/C++ 隔離應用程式和並存組件](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
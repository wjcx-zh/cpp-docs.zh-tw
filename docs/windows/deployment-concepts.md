---
title: 部署概念
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
ms.openlocfilehash: ac3565b4ec465ec60672d2238fbe81b71613a6c1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449035"
---
# <a name="deployment-concepts"></a>部署概念

本節將討論部署 C++ 應用程式的主要考量。

## <a name="windows-installer-deployment-in-c"></a>C + + 中的 Windows Installer 部署

Visual StudioC++專案通常使用傳統的 Windows 安裝程式安裝程式進行部署。 若要準備 Windows Installer 部署，您必須將應用程式封裝到 setup.exe 檔案，並連同安裝程式套件 (.msi) 散發該檔案。 然後，使用者會執行 setup.exe 來安裝應用程式。

您可以藉由將安裝專案新增至解決方案來封裝應用程式；建置時，它會建立散發給使用者的安裝程式和安裝程式套件檔案。 如需詳細資訊，請參閱[選擇部署方法](choosing-a-deployment-method.md)。

## <a name="library-dependencies"></a>程式庫相依性

當 C/C++ 應用程式使用 Visual C++ 程式庫所提供的功能建置時，將會取決於這些程式庫在執行階段是否存在。 為了要執行應用程式，它必須以靜態或動態方式連結至必要的 Visual C++ 程式庫。 如果應用程式以動態方式連結至 Visual C++ 程式庫，則在應用程式執行時該程式庫必須存在，以便進行載入。 相反地，如果應用程式以靜態方式連結至 Visual C++ 程式庫，使用者電腦上就不需要有對應的 DLL。 不過，靜態連結有一些負面影響 (例如增加應用程式檔案的大小)，可能使進行維護變得更加困難。 如需詳細資訊，請參閱[使用 DLL 的優點](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls)。

## <a name="packaging-and-redistributing"></a>封裝和轉散發

Visual C++ 程式庫會封裝為 DLL，並由 Visual Studio 在開發人員的電腦上安裝 C/C++ 應用程式的所有必要程式庫。 不過，將應用程式部署到使用者時，在大部分的情況下，要求他們安裝 Visual Studio 以執行應用程式並不可行。 請務必要能夠只轉散發應用程式正確執行所需的 Visual C++ 部分。

如需封裝和轉散發的詳細資訊，請參閱下列主題：

- [決定要轉散發哪些 DLL](determining-which-dlls-to-redistribute.md)。

- [選擇部署方法](choosing-a-deployment-method.md)。

- [通用 CRT 部署](universal-crt-deployment.md)。

如需部署範例和疑難排解的相關建議，請參閱：

- [部署範例](deployment-examples.md)。

- [針對 C/C++ 隔離應用程式和並存組件進行疑難排解](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。

## <a name="see-also"></a>另請參閱

- [部署傳統型應用程式](deploying-native-desktop-applications-visual-cpp.md)
- [了解 Visual C++ 應用程式的相依性](understanding-the-dependencies-of-a-visual-cpp-application.md)

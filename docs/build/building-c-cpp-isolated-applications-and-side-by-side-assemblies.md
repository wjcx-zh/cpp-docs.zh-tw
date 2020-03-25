---
title: 建置 C/C++ 隔離應用程式和並存組件
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: db2978c054362b6c329fb786d0f7da322d4c9201
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169873"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>建置 C/C++ 隔離應用程式和並存組件

Visual Studio 根據[隔離的應用程式](/windows/win32/SbsCs/isolated-applications)和[並存元件](/windows/win32/SbsCs/about-side-by-side-assemblies-)的概念，支援 Windows 用戶端應用程式的部署模型。 根據預設，Visual Studio 會將所有的原C++生 C/應用程式建立為隔離的應用程式，以C++使用[資訊清單](/windows/win32/sbscs/manifests)來描述其對 Visual 程式庫的相依性

將 C/C++ 程式建置為隔離應用程式會帶來很多好處。 例如，當其他 C/C++ 應用程式安裝或解除安裝 Visual C++ 程式庫時，不會影響到隔離應用程式。 隔離的應用程式所使用的 Visual C++ 程式庫可能仍會在應用程式的本機資料夾轉散發，或者由安裝轉散發至原生組件快取 (WinSxS) 中；不過，使用 [發行者組態檔](/windows/win32/SbsCs/publisher-configuration)可簡化提供已部署應用程式的 Visual C++ 程式庫。 隔離應用程式部署模型可更輕鬆地確保在特定電腦上執行的 C/C++ 應用程式，使用最新版本的 Visual C++ 程式庫，同時仍保留系統管理員和應用程式作者可控制將應用程式的版本，明確繫結至其相依 DLL 的可能性。

本節討論您可以如何將 C/C++ 應用程式建置為隔離應用程式，並確保其使用資訊清單，繫結至 Visual C++ 程式庫。 本節中的資訊主要適用于原生或未受管理C++的應用程式。 如需部署以 Visual Studio C++建立的原生應用程式的詳細資訊，請參閱轉散發[視覺效果C++ ](../windows/redistributing-visual-cpp-files.md)檔案。

## <a name="in-this-section"></a>本節內容

[隔離應用程式和並存組件的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[建置C/C++ 隔離應用程式](building-c-cpp-isolated-applications.md)

[建置 C/C++ 並存組件](building-c-cpp-side-by-side-assemblies.md)

[如何：建置免註冊的 COM 元件](how-to-build-registration-free-com-components.md)

[如何：建置隔離的應用程式以使用 COM 元件](how-to-build-isolated-applications-to-consume-com-components.md)

[了解 C/C++ 程式的資訊清單產生過程](understanding-manifest-generation-for-c-cpp-programs.md)

[疑難排解 C/C++ 隔離應用程式和並存組件](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>相關章節

[隔離應用程式和並存組件](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[部署桌面應用程式](../windows/deploying-native-desktop-applications-visual-cpp.md)

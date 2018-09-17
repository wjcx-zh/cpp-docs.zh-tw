---
title: 建置 C/c + + 隔離應用程式和並排顯示組件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b3327f4d0ae20b13c97ea0916e7a2c86e7006dd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710095"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>建置 C/C++ 隔離應用程式和並存組件

Visual c + + 的概念為基礎的 Windows 用戶端應用程式支援的部署模型[隔離應用程式](/windows/desktop/SbsCs/isolated-applications)並[並排顯示組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 根據預設，Visual c + + 建置所有的原生 C/c + + 應用程式使用的為隔離應用程式[資訊清單](https://msdn.microsoft.com/library/aa375365)來描述其相依性 Visual c + + 程式庫。

將 C/C++ 程式建置為隔離應用程式會帶來很多好處。 例如，當其他 C/C++ 應用程式安裝或解除安裝 Visual C++ 程式庫時，不會影響到隔離應用程式。 隔離的應用程式所使用的 visual c + + 程式庫仍可轉散發在其中一個應用程式的本機資料夾中，或安裝程式對原生組件快取 (WinSxS);不過，服務的 Visual c + + 程式庫，針對已部署應用程式可以藉由簡化[發行者組態檔](/windows/desktop/SbsCs/publisher-configuration)。 隔離應用程式部署模型可更輕鬆地確保在特定電腦上執行的 C/C++ 應用程式，使用最新版本的 Visual C++ 程式庫，同時仍保留系統管理員和應用程式作者可控制將應用程式的版本，明確繫結至其相依 DLL 的可能性。

本節討論您可以如何將 C/C++ 應用程式建置為隔離應用程式，並確保其使用資訊清單，繫結至 Visual C++ 程式庫。 本節中的資訊主要適用於原生或 Unmanaged Visual C++ 應用程式。 如需部署使用 Visual C++ 建置之原生應用程式的資訊，請參閱 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。

## <a name="in-this-section"></a>本節內容

[隔離應用程式和並存組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[建置C/C++ 隔離應用程式](../build/building-c-cpp-isolated-applications.md)

[建置 C/C++ 並存組件](../build/building-c-cpp-side-by-side-assemblies.md)

[如何：建置免註冊的 COM 元件](../build/how-to-build-registration-free-com-components.md)

[如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)

[了解 C/C++ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)

[疑難排解 C/C++ 隔離應用程式和並存組件](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>相關章節

[隔離的應用程式和並排顯示組件](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)
---
title: "建置 C/c + + 隔離應用程式和-並存組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5dec3b0db6d77cc11d0e2ccdc97fe54ab8e0624
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>建置 C/C++ 隔離應用程式和並存組件
Visual C++ 基於 [隔離的應用程式](http://msdn.microsoft.com/library/aa375190) 和 [並存組件](http://msdn.microsoft.com/library/ff951640)的想法，支援 Windows 用戶端應用程式的部署模型。 根據預設，Visual C++ 會將所有原生 C/C++ 應用程式，建置為隔離的應用程式，以使用 [資訊清單](http://msdn.microsoft.com/library/aa375365) ，來描述其在 Visual C++ 程式庫上的相依性。  
  
 將 C/C++ 程式建置為隔離應用程式會帶來很多好處。 例如，當其他 C/C++ 應用程式安裝或解除安裝 Visual C++ 程式庫時，不會影響到隔離應用程式。 隔離的應用程式所使用的 Visual C++ 程式庫可能仍會在應用程式的本機資料夾轉散發，或者由安裝轉散發至原生組件快取 (WinSxS) 中；不過，使用 [發行者組態檔](http://msdn.microsoft.com/library/aa375680)可簡化提供已部署應用程式的 Visual C++ 程式庫。 隔離應用程式部署模型可更輕鬆地確保在特定電腦上執行的 C/C++ 應用程式，使用最新版本的 Visual C++ 程式庫，同時仍保留系統管理員和應用程式作者可控制將應用程式的版本，明確繫結至其相依 DLL 的可能性。  
  
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
 [隔離應用程式和並存組件](http://msdn.microsoft.com/library/dd408052)  
  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)
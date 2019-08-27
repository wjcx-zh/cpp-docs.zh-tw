---
title: 建置 C/C++ 隔離應用程式
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493336"
---
# <a name="building-cc-isolated-applications"></a>建置 C/C++ 隔離應用程式

隔離的應用程式只會相依于並存元件, 並使用資訊清單系結至其相依性。 您的應用程式不需要完全隔離, 就能在 Windows 上正常執行。不過, 藉由投資讓應用程式完全隔離, 您可以在未來需要為應用程式提供服務時節省時間。 如需讓應用程式完全隔離的優點詳細資訊, 請參閱[隔離的應用程式](/windows/win32/SbsCs/isolated-applications)。

當您使用 Visual Studio 建立原生C++ C/應用程式時, Visual Studio 專案系統預設會產生資訊清單檔, 以描述應用程式在 Visual Studio 程式庫上的相依性。 如果這些是您的應用程式所擁有的唯一相依性, 則會在使用 Visual Studio 重建時, 立即成為隔離的應用程式。 如果您的應用程式在執行時間使用其他程式庫, 則您可能需要遵循[建立 C/C++並存元件](building-c-cpp-side-by-side-assemblies.md)中所述的步驟, 將這些程式庫重建為並存元件。

## <a name="see-also"></a>另請參閱

[隔離應用程式和並存組件的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[建置 C/C++ 隔離應用程式和並存組件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

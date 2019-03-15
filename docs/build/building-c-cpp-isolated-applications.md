---
title: 建置 C/C++ 隔離應用程式
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: e02fec4115d328dd8230d68ddb65b380ec743dc0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815199"
---
# <a name="building-cc-isolated-applications"></a>建置 C/C++ 隔離應用程式

隔離的應用程式只依賴並排顯示組件，並繫結至其使用資訊清單的相依性。 您不需要您的應用程式是完全隔離，才能在 Windows; 上正確執行不過，藉由投資讓您完全隔離的應用程式，如果您需要服務您的應用程式中未來可能節省時間。 讓您完全隔離的應用程式的優點詳細資訊，請參閱[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)。

當您建置原生 C/c + + 應用程式使用 Visual c + + 時，根據預設 Visual Studio 專案系統會產生資訊清單檔，以描述您的應用程式相依於 Visual c + + 程式庫。 如果這些是唯一的相依性應用程式有，則它會變成隔離的應用程式，只要它使用 Visual Studio 重新建置。 如果您的應用程式在執行階段，使用其他程式庫，則您可能需要重建這些程式庫做為並排顯示組件中所述的步驟[建置 C/c + +-並存組件](building-c-cpp-side-by-side-assemblies.md)。

## <a name="see-also"></a>另請參閱

[隔離應用程式和並存組件的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[建置 C/C++ 隔離應用程式和並存組件](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

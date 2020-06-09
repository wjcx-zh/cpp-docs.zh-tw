---
title: 在架構上建置
ms.date: 11/04/2016
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
ms.openlocfilehash: 2c171b223892c8bca1b32e18c57c09027558c192
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619725"
---
# <a name="building-on-the-framework"></a>在架構上建置

您在使用 MFC 架構設定應用程式的角色是提供應用程式特定的原始程式碼，並藉由定義要回應的訊息和命令來連接元件。 您可以使用 c + + 語言和標準 c + + 技術，從類別庫所提供的類別衍生您自己的應用程式特定類別，以及覆寫和擴充基類的行為。

在相關主題中，下表說明您通常會遵循的一般作業順序，以及您的責任與架構的責任：

- [使用架構建置應用程式的順序](sequence-of-operations-for-building-mfc-applications.md)

- [建立 OLE 應用程式的作業順序](sequence-of-operations-for-creating-ole-applications.md)

- [建立 ActiveX 控制項的作業順序](sequence-of-operations-for-creating-activex-controls.md)

- [建立資料庫應用程式的作業順序](sequence-of-operations-for-creating-database-applications.md)

在大部分的情況下，您可以遵循這些資料表做為建立 MFC 應用程式的一系列步驟，雖然某些步驟是替代選項。 例如，大部分的應用程式會從可用的數種類型中使用某種類型的 view 類別。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](general-mfc-topics.md)

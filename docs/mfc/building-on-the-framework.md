---
title: 在架構上建置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application-specific classes [MFC]
- application framework [MFC], building applications
- applications [MFC]
- MFC, application development
ms.assetid: 883f0f19-866f-4221-8a3d-5607941dc8d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca0ebd9bf03df8725c14df8d2aca1f7858b7b65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396177"
---
# <a name="building-on-the-framework"></a>在架構上建置

您在使用 MFC 架構中設定應用程式的角色是提供特定應用程式的原始程式碼，並藉由定義訊息和回應的命令來連接元件。 您可以從所提供的類別庫衍生您自己的應用程式特定類別，還是覆寫，並擴大基底類別的行為中使用的 c + + 語言和標準 c + + 技術。

相關主題，在下表說明您通常會執行的作業和您的責任與架構的責任的一般順序：

- [建置使用 Framework 的應用程式的順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)

- [建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)

- [建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)

- [建立資料庫應用程式的作業順序](../mfc/sequence-of-operations-for-creating-database-applications.md)

大部分的情況下，您可以依照這些資料表以一連串的步驟建立 MFC 應用程式，雖然某些步驟是替代選項。 例如，大部分的應用程式使用一種類型的檢視類別，從數個可用的類型。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)


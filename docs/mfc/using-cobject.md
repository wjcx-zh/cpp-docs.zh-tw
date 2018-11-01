---
title: 使用 CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: 443a381c33458e61ba49eb10724d31614831f422
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564823"
---
# <a name="using-cobject"></a>使用 CObject

[CObject](../mfc/reference/cobject-class.md)是適用於大部分的 Microsoft Foundation Class 程式庫 (MFC) 的根的基底類別。 `CObject`類別包含許多實用的功能，您可能想要併入您自己的程式物件，包括序列化支援、 執行階段類別資訊，以及物件的診斷輸出。 如果您衍生您的類別，從`CObject`，您的類別可以利用這些弱點`CObject`功能。

## <a name="what-do-you-want-to-do"></a>您要做什麼

- [從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)

- [將執行階段類別資訊、 動態建立和序列化的支援新增至我在衍生類別](../mfc/specifying-levels-of-functionality.md)

- [存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)

- [動態建立物件](../mfc/dynamic-object-creation.md)

- [傾印物件的資料，供診斷之用](/previous-versions/visualstudio/visual-studio-2010/sc15kz85)

- 驗證物件的內部狀態 (請參閱[MFC ASSERT_VALID 和 CObject::AssertValid](reference/diagnostic-services.md#assert_valid))

- [有永續性儲存體序列化本身的類別](../mfc/serialization-in-mfc.md)

- 看到一份[CObject 常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass 結構](../mfc/reference/cruntimeclass-structure.md)<br/>
[檔案](../mfc/files-in-mfc.md)<br/>
[序列化](../mfc/serialization-in-mfc.md)


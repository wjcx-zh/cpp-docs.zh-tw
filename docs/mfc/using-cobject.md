---
title: 使用 CObject
ms.date: 11/04/2016
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
ms.openlocfilehash: b5399f02819407a529fd5ec66d4f5acbb16ca002
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441931"
---
# <a name="using-cobject"></a>使用 CObject

[CObject](../mfc/reference/cobject-class.md)是大部分 MFC 程式庫（MFC）的根基類。 `CObject` 類別包含許多有用的功能，您可能會想要將它們併入自己的程式物件中，包括序列化支援、執行時間類別資訊和物件診斷輸出。 如果您從 `CObject`衍生您的類別，您的類別可以利用這些 `CObject` 功能。

## <a name="what-do-you-want-to-do"></a>您想要做什麼

- [從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)

- [將執行時間類別資訊、動態建立和序列化的支援加入至我的衍生類別](../mfc/specifying-levels-of-functionality.md)

- [存取執行時間類別資訊](../mfc/accessing-run-time-class-information.md)

- [動態建立物件](../mfc/dynamic-object-creation.md)

- [傾印物件的資料以供診斷之用](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))

- 驗證物件的內部狀態（請參閱[MFC ASSERT_VALID 和 CObject：： AssertValid](reference/diagnostic-services.md#assert_valid)）

- [將類別序列化為持續性儲存體](../mfc/serialization-in-mfc.md)

- 查看[CObject 常見問題](../mfc/cobject-class-frequently-asked-questions.md)的清單

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass 結構](../mfc/reference/cruntimeclass-structure.md)<br/>
[檔案](../mfc/files-in-mfc.md)<br/>
[序列化](../mfc/serialization-in-mfc.md)

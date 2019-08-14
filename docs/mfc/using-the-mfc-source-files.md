---
title: 使用 MFC 原始程式檔
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980495"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 原始程式檔

MFC 程式庫提供完整的原始程式碼。 標頭檔 (.h) 位於 \atlmfc\include 目錄中，實作檔 (.cpp) 位於 \atlmfc\src\mfc 目錄。

這一系列的文章將說明 MFC 用來註解每個類別各部分的慣例、這些註解的方法，以及您在每一個區段中預期應該找到的內容。 Visual C++ 精靈針對將為您建立的類別使用類似的慣例，因此，您可能會發現這些慣例有助於您的程式碼。

您可能已熟悉**公用**、**受保護**和**私** C++用關鍵字。 在 MFC 標頭檔中, 您會發現每個類別可能會有其中的幾個。 例如, 公用成員變數和函數可能會在一個以上的**公用**關鍵字底下。 這是因為 MFC 會根據其使用來分隔成員變數和函式, 而不是依據允許的存取類型。 MFC 會謹慎使用**私**用。 即使是視為執行詳細資料的專案, 通常還是會**受到保護**, 而且許多次都是**公用**的。 雖然不鼓勵存取實作細節，但 MFC 將決定權保留給您。

在 mfc 應用程式精靈所建立的 MFC 原始程式檔和標頭檔中, 您可以在類別宣告 (通常是依此順序) 中找到如下的批註:

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

此系列文章中涵蓋的主題：

- [批註的範例](../mfc/an-example-of-the-comments.md)

- [執行批註](../mfc/decrement-implementation-comment.md)

- [函數描述](../mfc/decrement-constructors-comment.md)

- [屬性批註](../mfc/decrement-attributes-comment.md)

- [作業批註](../mfc/decrement-operations-comment.md)

- [Overridables 批註](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)

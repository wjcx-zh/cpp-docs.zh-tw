---
title: 可覆寫的 CWinApp 成員函式
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 28ba243bd755e25db5f2cb03d08013f082fbc918
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447259"
---
# <a name="overridable-cwinapp-member-functions"></a>可覆寫的 CWinApp 成員函式

[CWinApp](../mfc/reference/cwinapp-class.md)提供數個關鍵可覆寫成員函式（`CWinApp` 會從 `CWinApp` 衍生的類別[CWinThread](../mfc/reference/cwinthread-class.md)覆寫這些成員）：

- [InitInstance](../mfc/initinstance-member-function.md)

- [執行](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

唯一您必須覆寫的 `CWinApp` 成員函式是 `InitInstance`。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)

---
title: 可覆寫的 CWinApp 成員函式
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 9f1098e305606df9463e308466b7864b019d5a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459275"
---
# <a name="overridable-cwinapp-member-functions"></a>可覆寫的 CWinApp 成員函式

[CWinApp](../mfc/reference/cwinapp-class.md)提供數個金鑰可覆寫成員函式 (`CWinApp`類別中的這些成員會覆寫[CWinThread](../mfc/reference/cwinthread-class.md)，從中`CWinApp`衍生):

- [InitInstance](../mfc/initinstance-member-function.md)

- [執行](../mfc/run-member-function.md)

- [ExitInstance](../mfc/exitinstance-member-function.md)

- [OnIdle](../mfc/onidle-member-function.md)

唯一您必須覆寫的 `CWinApp` 成員函式是 `InitInstance`。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)

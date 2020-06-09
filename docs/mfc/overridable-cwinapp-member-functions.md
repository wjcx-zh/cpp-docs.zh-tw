---
title: 可覆寫的 CWinApp 成員函式
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 7ae72a52c37582f8398ebc03f404ff105fe14650
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624005"
---
# <a name="overridable-cwinapp-member-functions"></a>可覆寫的 CWinApp 成員函式

[CWinApp](reference/cwinapp-class.md)提供數個關鍵可覆寫成員函式（ `CWinApp` 從衍生的類別[CWinThread](reference/cwinthread-class.md)覆寫這些成員 `CWinApp` ）：

- [InitInstance](initinstance-member-function.md)

- [執行](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

唯一您必須覆寫的 `CWinApp` 成員函式是 `InitInstance`。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](cwinapp-the-application-class.md)

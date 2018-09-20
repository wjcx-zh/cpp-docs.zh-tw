---
title: 可覆寫的 CWinApp 成員函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ced9d7d5f7f49df50e028a299f83ddebdc9fc2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395118"
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

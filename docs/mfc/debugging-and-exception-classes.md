---
title: 偵錯和例外狀況類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 5549ea3e67f06e82e441c1ca5afc4a1b859dd410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587964"
---
# <a name="debugging-and-exception-classes"></a>偵錯和例外狀況類別

這些類別會提供偵錯動態記憶體配置的支援，以及從擲回例外狀況的函式傳遞例外狀況資訊至攔截例外狀況函式的支援。

使用類別[CDumpContext](../mfc/reference/cdumpcontext-class.md)並[CMemoryState](../mfc/reference/cmemorystate-structure.md)在開發期間協助偵錯，如中所述[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。 使用[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)若要在執行階段，判斷任何物件的類別，如本文所述[存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)。 架構會使用 `CRuntimeClass` 動態建立特定類別的物件。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)


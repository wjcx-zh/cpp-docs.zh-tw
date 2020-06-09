---
title: 偵錯和例外狀況類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 6c7d1fc20556993c3c6690122786d7a767d895ad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625942"
---
# <a name="debugging-and-exception-classes"></a>偵錯和例外狀況類別

這些類別會提供偵錯動態記憶體配置的支援，以及從擲回例外狀況的函式傳遞例外狀況資訊至攔截例外狀況函式的支援。

在開發期間使用類別[CDumpCoNtext](reference/cdumpcontext-class.md)和[CMemoryState](reference/cmemorystate-structure.md) ，以協助進行偵錯工具，如[調試 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)中所述。 您可以使用[CRuntimeClass](reference/cruntimeclass-structure.md) ，在執行時間判斷任何物件的類別，如[存取執行時間類別資訊](accessing-run-time-class-information.md)一文中所述。 架構會使用 `CRuntimeClass` 動態建立特定類別的物件。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)

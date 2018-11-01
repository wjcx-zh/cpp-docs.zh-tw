---
title: 動態物件建立
ms.date: 11/04/2016
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 75d4a055f047abfcac4451c04bcd1cc75650c89a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563718"
---
# <a name="dynamic-object-creation"></a>動態物件建立

本文說明如何在執行階段動態建立物件。 程序會使用執行階段類別資訊，如本文所述[存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)。

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>動態建立指定其為執行階段類別的物件

1. 使用下列程式碼，透過 `CreateObject` 的 `CRuntimeClass` 函式動態建立物件。 請注意，在失敗時，`CreateObject`會傳回**NULL**而非引發例外狀況：

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CObject](../mfc/using-cobject.md)


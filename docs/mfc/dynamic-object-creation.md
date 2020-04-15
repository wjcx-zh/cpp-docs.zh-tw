---
title: 動態物件建立
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364800"
---
# <a name="dynamic-object-creation"></a>動態物件建立

本文說明如何在執行階段動態建立物件。 該過程使用運行時類資訊,如[訪問運行時類資訊](../mfc/accessing-run-time-class-information.md)一文中所述。

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>在執行時類別中動態建立物件

1. 使用以下代碼使用的`CreateObject`函數動態創建物件。 `CRuntimeClass` 發生故障時,`CreateObject`傳回**NULL**而不是引發異常:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>另請參閱

[Destroying Window Objects](tn017-destroying-window-objects.md)使用[CObject](using-cobject.md)銷毀視窗物件


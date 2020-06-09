---
title: 動態物件建立
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 00e627e6d73e510ca694966291e2ef518fef18b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619540"
---
# <a name="dynamic-object-creation"></a>動態物件建立

本文說明如何在執行階段動態建立物件。 此程式會使用執行時間類別資訊，如[存取執行時間類別資訊](accessing-run-time-class-information.md)一文中所述。

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>以動態方式建立物件，指定其執行時間類別

1. 使用下列程式碼，利用的函式動態建立物件 `CreateObject` `CRuntimeClass` 。 失敗時，會傳回 `CreateObject` **Null** ，而不會引發例外狀況：

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>另請參閱

終結[視窗物件](tn017-destroying-window-objects.md) 
[使用 CObject](using-cobject.md)

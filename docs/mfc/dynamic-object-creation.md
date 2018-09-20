---
title: 動態物件建立 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19f6a895eb48b3ae1816edc45747c865e7e03b96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420149"
---
# <a name="dynamic-object-creation"></a>動態物件建立

本文說明如何在執行階段動態建立物件。 程序會使用執行階段類別資訊，如本文所述[存取執行階段類別資訊](../mfc/accessing-run-time-class-information.md)。

#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>動態建立指定其為執行階段類別的物件

1. 使用下列程式碼，透過 `CreateObject` 的 `CRuntimeClass` 函式動態建立物件。 請注意，在失敗時，`CreateObject`會傳回**NULL**而非引發例外狀況：

     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CObject](../mfc/using-cobject.md)


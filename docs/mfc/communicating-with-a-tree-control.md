---
title: 與樹狀目錄控制項通訊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78bb6a6d6421a5336f8efbffc7d24a6121e208e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432148"
---
# <a name="communicating-with-a-tree-control"></a>與樹狀目錄控制項通訊

您可以使用不同的方法呼叫成員函式[CTreeCtrl](../mfc/reference/ctreectrl-class.md)根據物件的建立方式的物件：

- 如果樹狀目錄控制項位於對話方塊中，請使用您在對話方塊類別中建立之 `CTreeCtrl` 類型的成員變數。

- 如果樹狀目錄控制項是一個子視窗，請使用您用來建構物件的 `CTreeCtrl` 物件 (或指標)。

- 如果您使用`CTreeView`物件，請使用此函式[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)取得樹狀目錄控制項的參考。 您可以使用這個值初始化其他參考或指派參考的位址給 `CTreeCtrl` 指標。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


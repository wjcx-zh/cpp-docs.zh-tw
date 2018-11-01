---
title: 與樹狀目錄控制項通訊
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654177"
---
# <a name="communicating-with-a-tree-control"></a>與樹狀目錄控制項通訊

您可以使用不同的方法呼叫成員函式[CTreeCtrl](../mfc/reference/ctreectrl-class.md)根據物件的建立方式的物件：

- 如果樹狀目錄控制項位於對話方塊中，請使用您在對話方塊類別中建立之 `CTreeCtrl` 類型的成員變數。

- 如果樹狀目錄控制項是一個子視窗，請使用您用來建構物件的 `CTreeCtrl` 物件 (或指標)。

- 如果您使用`CTreeView`物件，請使用此函式[ctreeview:: Gettreectrl](../mfc/reference/ctreeview-class.md#gettreectrl)取得樹狀目錄控制項的參考。 您可以使用這個值初始化其他參考或指派參考的位址給 `CTreeCtrl` 指標。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


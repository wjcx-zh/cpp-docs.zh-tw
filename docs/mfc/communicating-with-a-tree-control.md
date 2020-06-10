---
title: 與樹狀目錄控制項通訊
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: f480cdad2fce53f830b8067083a8a4be4b4e4848
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619653"
---
# <a name="communicating-with-a-tree-control"></a>與樹狀目錄控制項通訊

根據物件的建立方式而定，您可以使用不同的方法來呼叫[CTreeCtrl](reference/ctreectrl-class.md)物件中的成員函式：

- 如果樹狀目錄控制項位於對話方塊中，請使用您在對話方塊類別中建立之 `CTreeCtrl` 類型的成員變數。

- 如果樹狀目錄控制項是一個子視窗，請使用您用來建構物件的 `CTreeCtrl` 物件 (或指標)。

- 如果您使用的是 `CTreeView` 物件，請使用[CTreeView：： GetTreeCtrl](reference/ctreeview-class.md#gettreectrl)函式取得樹狀目錄控制項的參考。 您可以使用這個值初始化其他參考或指派參考的位址給 `CTreeCtrl` 指標。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](using-ctreectrl.md)<br/>
[控制項](controls-mfc.md)

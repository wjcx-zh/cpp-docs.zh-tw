---
title: 使用熱鍵控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be0d27016204724672c23f04fdee38f01b69e6a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372286"
---
# <a name="using-a-hot-key-control"></a>使用熱鍵控制項

熱鍵控制項的一般用法會遵循下列模式：

- 建立控制項。 如果在對話方塊範本中指定控制項，就會隨對話方塊的建立而自動建立。 (您應該[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)您對應至熱鍵控制項的對話方塊類別中的成員。)或者，您可以使用[建立](../mfc/reference/chotkeyctrl-class.md#create)做為任何視窗的子視窗建立控制項的成員函式。

- 如果您想要設定控制項的預設值，呼叫[SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey)成員函式。 如果您想要禁止特定內含移位狀態中，呼叫[SetRules](../mfc/reference/chotkeyctrl-class.md#setrules)。 若要這樣做的好時機是在對話方塊中的控制項在對話方塊中， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式。

- 使用者與控制項互動熱鍵控制項有焦點時按下快速鍵的索引鍵組合。 使用者則以某種方式表示，這項工作完成時，可能是透過按鈕在對話方塊中。

- 當您的程式會通知使用者已選取的便捷鍵時，它應該使用此成員函式[GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey)從熱鍵控制項擷取虛擬索引鍵和 shift 狀態值。

- 一旦您知道什麼索引鍵選取的使用者，您可以設定使用其中一個方法中所述的熱鍵[設定熱鍵](../mfc/setting-a-hot-key.md)。

- 熱鍵控制項是否在對話方塊中，它和`CHotKeyCtrl`物件將會自動終結。 否則，您必須確保控制項和 `CHotKeyCtrl` 物件都已正確地終結。

## <a name="see-also"></a>另請參閱

[使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


---
title: 建立狀態列的方法
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: 9bdaa76dc68467dce1021d9b5f54eaafa248c529
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624264"
---
# <a name="methods-of-creating-a-status-bar"></a>建立狀態列的方法

MFC 提供兩個建立狀態列的類別： [CStatusBar](reference/cstatusbar-class.md)和[CStatusBarCtrl](reference/cstatusbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CStatusBar`提供狀態列通用控制項的所有功能，它會自動與功能表和工具列互動，並為您處理許多必要的通用控制項設定和結構;不過，產生的可執行檔通常會比使用建立的還大 `CStatusBarCtrl` 。

`CStatusBarCtrl`通常會產生較小的可執行檔， `CStatusBarCtrl` 如果您不想要將狀態列整合到 MFC 架構中，您可能會想要使用。 如果您打算使用 `CStatusBarCtrl` 並將狀態列整合到 mfc 架構中，則必須特別小心地將狀態列控制項操作傳達給 mfc。 這種通訊並不容易;不過，當您使用時，這是不需要的額外工作 `CStatusBar` 。

Visual C++ 提供兩種方式來利用狀態列通用控制項。

- 使用建立狀態列 `CStatusBar` ，然後呼叫[CStatusBar：： GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl)以取得成員函式的存取權 `CStatusBarCtrl` 。

- 使用[CStatusBarCtrl](reference/cstatusbarctrl-class.md)的函式建立狀態列。

任一種方法都可讓您存取狀態列控制項的成員函式。 當您呼叫 `CStatusBar::GetStatusBarCtrl`時，會傳回 `CStatusBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 如需使用來建立和建立狀態列的詳細資訊，請參閱[CStatusBar](reference/cstatusbar-class.md) `CStatusBar` 。

## <a name="see-also"></a>另請參閱

[使用 CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[控制項](controls-mfc.md)

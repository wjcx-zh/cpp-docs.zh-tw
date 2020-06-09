---
title: 將項目加入至標題控制項
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616459"
---
# <a name="adding-items-to-the-header-control"></a>將項目加入至標題控制項

在其父視窗中建立標題控制項（[CHeaderCtrl](reference/cheaderctrl-class.md)）之後，請視需要加入多個「標頭專案」：通常每個資料行一個。

### <a name="to-add-a-header-item"></a>若要加入標題項目

1. 準備[HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構。

1. 呼叫[CHeaderCtrl：： InsertItem](reference/cheaderctrl-class.md#insertitem)，傳遞結構。

1. 針對其他項目重複步驟 1 和 2。

如需詳細資訊，請參閱在 Windows SDK 中[將專案新增至標題控制項](/windows/win32/Controls/header-controls)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](using-cheaderctrl.md)<br/>
[控制項](controls-mfc.md)

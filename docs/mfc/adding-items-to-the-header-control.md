---
title: 將項目加入至標題控制項
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 9b1cfd6f94d6412eef7b2bb9820f712e2a335454
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741178"
---
# <a name="adding-items-to-the-header-control"></a>將項目加入至標題控制項

在其父視窗中建立標題控制項（[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)）之後，請視需要加入多個「標頭專案」：通常每個資料行一個。

### <a name="to-add-a-header-item"></a>若要加入標題項目

1. 準備[HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構。

1. 呼叫[CHeaderCtrl：： InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem)，傳遞結構。

1. 針對其他項目重複步驟 1 和 2。

如需詳細資訊，請參閱在 Windows SDK 中[將專案新增至標題控制項](/windows/win32/Controls/header-controls)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

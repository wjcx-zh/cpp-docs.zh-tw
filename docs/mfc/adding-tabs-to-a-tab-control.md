---
title: 將索引標籤加入至索引標籤控制項
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 89132e94396b51bee4a111b963c67d029f3dd9df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616525"
---
# <a name="adding-tabs-to-a-tab-control"></a>將索引標籤加入至索引標籤控制項

建立索引標籤控制項（[CTabCtrl](reference/ctabctrl-class.md)）之後，請視需要新增多個索引標籤。

### <a name="to-add-a-tab-item"></a>若要加入索引標籤項目

1. 準備[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構。

1. 呼叫[CTabCtrl：： InsertItem](reference/ctabctrl-class.md#insertitem)，傳遞結構。

1. 對其他索引標籤項目重複步驟 1 和 2。

如需詳細資訊，請參閱在 Windows SDK 中[建立索引標籤控制項](/windows/win32/Controls/tab-controls)。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](using-ctabctrl.md)<br/>
[控制項](controls-mfc.md)

---
title: 將控制項加入至屬性工作表
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 527c0a5ef6e9dc4fcc9d7668c12e15ec956b0e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616065"
---
# <a name="adding-controls-to-a-property-sheet"></a>將控制項加入至屬性工作表

根據預設，屬性工作表會配置視窗區域給屬性頁、索引標籤索引和 [確定]、[取消] 和 [套用] 按鈕  （非模式屬性工作表沒有 [確定]、[取消] 和 [套用] 按鈕）。您可以將其他控制項新增至屬性工作表。 例如，如果套用至外部物件，您可以在屬性頁區域右邊加入預覽視窗，向使用者顯示目前設定的外觀。

您可以在 `OnCreate` 處理常式中將控制項加入屬性工作表對話方塊。 包容的其他控制項通常需要擴大屬性工作表對話方塊的大小。 呼叫基類**CPropertySheet：： OnCreate**之後，呼叫[GetWindowRect](reference/cwnd-class.md#getwindowrect)以取得目前所配置屬性工作表視窗的寬度和高度，展開矩形的維度，然後呼叫[MoveWindow](reference/cwnd-class.md#movewindow)以變更屬性工作表視窗的大小。

## <a name="see-also"></a>另請參閱

[屬性工作表](property-sheets-mfc.md)<br/>
[CPropertyPage 類別](reference/cpropertypage-class.md)<br/>
[CPropertySheet 類別](reference/cpropertysheet-class.md)

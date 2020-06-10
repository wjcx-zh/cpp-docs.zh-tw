---
title: 終結清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: d128a613a2a4cb595f362f843a5ae2eba830e538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621905"
---
# <a name="destroying-the-list-control"></a>終結清單控制項

如果您將[CListCtrl](reference/clistctrl-class.md)物件內嵌為 view 或 dialog 類別的資料成員，它會在其擁有者終結時終結。 如果您使用[CListView](reference/clistview-class.md)，架構會在終結視圖時終結控制項。

如果您對於要儲存在應用程式中的某些清單資料而非清單控制項進行配置，則必須為其解除配置進行安排。 如需詳細資訊，請參閱 Windows SDK 中的[回呼專案和回呼遮罩](/windows/win32/Controls/using-list-view-controls)。

此外，您必須負責解除配置您所建立並與清單控制項關聯的所有影像清單。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)

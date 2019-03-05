---
title: 終結清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 963da9e6db2f0fe063dee1ca19ab23f545ed5e76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326708"
---
# <a name="destroying-the-list-control"></a>終結清單控制項

如果您在內嵌您[CListCtrl](../mfc/reference/clistctrl-class.md)做為資料成員，檢視或對話方塊類別的物件終結時終結其擁有者。 如果您使用[CListView](../mfc/reference/clistview-class.md)，架構會在終結檢視時終結控制項。

如果您對於要儲存在應用程式中的某些清單資料而非清單控制項進行配置，則必須為其解除配置進行安排。 如需詳細資訊，請參閱 <<c0> [ 回呼項目和回呼遮罩](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。

此外，您必須負責解除配置您所建立並與清單控制項關聯的所有影像清單。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

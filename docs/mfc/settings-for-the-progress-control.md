---
title: 進度控制項的設定
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 1960b15c2f76d7cbfc9f249a77481b795e6a27ea
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290747"
---
# <a name="settings-for-the-progress-control"></a>進度控制項的設定

進度控制項的基本設定 ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) 的範圍和目前的位置。 範圍表示作業的整個持續期間。 目前的位置表示您的應用程式已完成此作業的進度。 範圍或位置的任何變更會讓進度控制項重繪其本身。

根據預設，範圍會設定為 0-100，而初始位置設定為 0。 若要擷取進度控制項的目前的範圍設定，請使用[GetRange](../mfc/reference/cprogressctrl-class.md#getrange)成員函式。 若要變更的範圍，請使用[SetRange](../mfc/reference/cprogressctrl-class.md#setrange)成員函式。

若要設定的位置，使用[SetPos](../mfc/reference/cprogressctrl-class.md#setpos)。 若要擷取目前的位置而不需要指定新的值，請使用[GetPos](../mfc/reference/cprogressctrl-class.md#getpos)。 比方說，您可以直接查詢目前作業的狀態。

若要逐步進度控制項的目前位置，使用[StepIt](../mfc/reference/cprogressctrl-class.md#stepit)。 若要設定的每個步驟，使用[SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>另請參閱

[使用 CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

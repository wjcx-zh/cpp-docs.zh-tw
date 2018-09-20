---
title: 微調按鈕成員函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f00aedcf269996277c154f9dd051534a9c5e49
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431516"
---
# <a name="spin-button-member-functions"></a>微調按鈕成員函式

有數個成員函式可用來微調控制項 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md))。 請使用這些函式變更微調按鈕的下列屬性。

- **加速**您可以調整當使用者按住箭號按鈕時位置變更的速率。 若要加速功能，使用[SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel)並[GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel)成員函式。

- **基底**您可以變更的基底 （10 或 16） 用於顯示協同視窗標題中的位置。 若要使用的基底，使用[GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase)並[SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase)成員函式。

- **Buddy Window**可以動態設定協同視窗。 若要查詢或變更的控制項是協同視窗，使用[GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy)並[SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy)成員函式。

- **位置**您可以查詢，並變更位置。 若要直接與位置，使用[GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos)並[SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos)成員函式。 因為協同控制項的標題可能已經變更 (例如，當協同為編輯控制項時)，`GetPos` 會擷取目前標頭並調整位置。

- **範圍**您可以變更微調按鈕的最大和最小位置。 根據預設，最大值設定為 0，因此，最小值設定為 100。 因為預設最大值小於預設最小值，箭號按鈕的動作是違反直覺的。 一般而言，您將會設定範圍使用[SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)成員函式。 若要查詢範圍，請使用[GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange)。

## <a name="see-also"></a>另請參閱

[使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


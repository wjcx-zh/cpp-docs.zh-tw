---
title: 使用動畫控制項
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: fa5ce6cc30d4bc31dbe52c0e559ce97e40acacba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630993"
---
# <a name="using-an-animation-control"></a>使用動畫控制項

動畫控制項的一般用法會遵循下列模式：

- 建立控制項。 如果在對話方塊範本中指定控制項，就會隨對話方塊的建立而自動建立。 (您應該[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)您對應至動畫控制項的對話方塊類別中的成員。)或者，您可以使用[建立](../mfc/reference/canimatectrl-class.md#create)做為任何視窗的子視窗建立控制項的成員函式。

- 載入動畫控制項中的 AVI 短片，藉由呼叫[開啟](../mfc/reference/canimatectrl-class.md#open)成員函式。 在對話方塊類別的動畫控制項是否在對話方塊中，是要執行這項操作的好地方[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式。

- 藉由呼叫播放剪輯[播放](../mfc/reference/canimatectrl-class.md#play)成員函式。 在對話方塊類別的動畫控制項是否在對話方塊中，是要執行這項操作的好地方`OnInitDialog`函式。 呼叫`Play`不需要動畫控制項有 ACS_AUTOPLAY 樣式集。

- 如果您想要顯示剪輯的一部分，或播放它依框架，使用`Seek`成員函式。 若要停止正在播放的剪輯，請使用`Stop`成員函式。

- 如果您不立即終結控制項，從記憶體移除剪輯藉由呼叫`Close`成員函式。

- 如果動畫控制項在對話方塊中，它和`CAnimateCtrl`物件將會自動終結。 否則，您必須確保控制項和 `CAnimateCtrl` 物件都已正確地終結。 會自動終結控制項時，會關閉在播放 AVI 短片。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


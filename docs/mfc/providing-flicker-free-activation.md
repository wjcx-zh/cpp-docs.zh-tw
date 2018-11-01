---
title: 提供避免重繪閃動
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: d979a6f633926bed1ad59de86829b9ac27b0d0cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438138"
---
# <a name="providing-flicker-free-activation"></a>提供避免重繪閃動

如果您的控制項繪製本身相同的非作用中和作用中狀態 （並不會使用無視窗啟用），您可以避免繪製作業和之間非作用中的轉換時通常都會發生的視覺重繪與作用中狀態。 若要這樣做，請包含**noFlickerActivate**旗標所傳回的集合中的旗標[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如: 

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

如果您選取，將會自動產生的程式碼納入這個旗標**閃動**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面使用 [MFC ActiveX 控制項精靈] 建立您的控制項時。

如果您使用無視窗啟用，這個最佳化不會有作用。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)


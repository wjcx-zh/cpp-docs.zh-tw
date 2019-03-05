---
title: 使用未裁剪的裝置內容
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270666"
---
# <a name="using-an-unclipped-device-context"></a>使用未裁剪的裝置內容

如果您完全確定您的控制項不會繪製到其用戶端矩形之外，您也可以停用 `IntersectClipRect` 所進行的 `COleControl` 呼叫，以獲得小而可偵測的速度增益。 若要這樣做，請移除*colecontrol:: Getcontrolflags*旗標所傳回的旗標集中[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如: 

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

如果您選取要移除這個旗標的程式碼會自動產生**未裁剪的裝置內容**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面上，使用 [MFC ActiveX 控制項精靈] 建立您的控制項時。

如果您使用無視窗啟用，這個最佳化不會有作用。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

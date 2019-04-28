---
title: 非現用時提供滑鼠互動
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297121"
---
# <a name="providing-mouse-interaction-while-inactive"></a>非現用時提供滑鼠互動

如果未立即啟動您的控制項，您可能仍想它處理 WM_SETCURSOR 和 WM_MOUSEMOVE 訊息，即使控制項沒有自己的視窗。 這可藉由啟用`COleControl`的實作`IPointerInactive`介面，預設會停用。 (請參閱*ActiveX SDK*如需此介面的描述。)若要啟用它，pointerInactive 旗標的旗標所傳回的集合中包含[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

如果您選取，將會自動產生的程式碼納入這個旗標**滑鼠指標通知時非作用中**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面時建立您的控制項與**MFC ActiveX 控制項精靈**。

當`IPointerInactive`介面已啟用，容器會將委派 WM_SETCURSOR 和 WM_MOUSEMOVE 訊息。 `COleControl`實作`IPointerInactive`會透過您的控制項訊息對應的訊息分派之後適當調整滑鼠座標。 您可以將對應的項目加入至訊息對應處理的訊息，就像一般的視窗訊息。 在您為這些訊息的處理常式，請避免使用*m_hWnd*成員變數 （或任何成員函式，會使用它），其值不是先檢查**NULL**。

您也可以為 OLE 拖放操作目標的非現用控制項。 這需要啟用使用者拖曳物件時，目前的控制項，以便做為置放目標可以註冊控制項的視窗。 若要讓 啟用時間在拖曳期間，覆寫[COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)，並傳回 POINTERINACTIVE_ACTIVATEONDRAG 旗標：

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

啟用`IPointerInactive`介面通常表示您想要能夠隨時處理滑鼠訊息的控制項。 若要取得此行為在不支援的容器中`IPointerInactive`介面，您需要有控制項一律啟動時顯示，表示控制項應該包含在它的其他旗標的 OLEMISC_ACTIVATEWHENVISIBLE 旗標。 不過，若要避免這個旗標，從生效的容器中，支援`IPointerInactive`，您也可以指定 OLEMISC_IGNOREACTIVATEWHENVISIBLE 旗標：

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

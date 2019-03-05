---
title: 提供無視窗啟用
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 9d60c309d5644c106e6c85a0c7b3988916be7193
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284706"
---
# <a name="providing-windowless-activation"></a>提供無視窗啟用

視窗建立程式碼 (也就是當您呼叫時，會發生的一切`CreateWindow`) 會使執行。 維護螢幕上視窗的控制項必須管理視窗的訊息。 因此，無視窗控制項與視窗型控制項相較之下速度更快。

無視窗控制項與視窗型控制項不同的另一項優點在於，無視窗控制項支援透明繪製及非矩形螢幕區域。 常見的透明控制項範例是具有透明背景的文字控制項。 控制項會繪製文字，但不會繪製背景，因此文字後方的所有內容都可清楚看見。 新式的表單通常會採用非矩形控制項，例如箭號和圓形按鈕。

假設已寫入可支援無視窗物件的容器，控制項通常不需要自己的視窗，而是改用其容器的視窗服務。 無視窗控制項可與舊的容器回溯相容。 在未撰寫為支援無視窗控制項的舊容器中，無視窗控制項會在作用時建立視窗。

由於無視窗控制項沒有自己的視窗，因此具有視窗的容器會負責提供控制項自己的視窗所提供的服務。 例如，如果控制項需要查詢鍵盤焦點、擷取滑鼠或取得裝置內容，這些作業就會交由容器管理。 容器會使用 `IOleInPlaceObjectWindowless` 介面，將傳送至本身所屬視窗的使用者輸入訊息路由傳送至適當的無視窗控制項  (請參閱*ActiveX SDK*如需此介面的描述。)`COleControl`成員函式叫用這些服務與容器。

若要讓您使用無視窗啟用的控制項，包括**colecontrol:: Getcontrolflags**旗標所傳回的集合中的旗標[Clippaintdc](../mfc/reference/colecontrol-class.md#getcontrolflags)。 例如: 

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

如果您選取，將會自動產生的程式碼納入這個旗標**無視窗啟用**選項[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX 控制項精靈的頁面。

啟用無視窗啟用之後，容器會將輸入訊息委派至控制項的 `IOleInPlaceObjectWindowless` 介面。 這個介面的 `COleControl` 實作會在適當調整滑鼠座標之後，透過您控制項的訊息對應分派訊息。 您可以將對應的項目加入至訊息對應，如此就可以像處理一般視窗訊息一樣地處理訊息。 在您為這些訊息的處理常式，請避免使用*m_hWnd*成員變數 （或任何成員函式，會使用它），其值不是先檢查**NULL**。

`COleControl` 提供了適時從容器中叫用滑鼠擷取、鍵盤焦點、捲動和其他視窗服務的成員函式，包括：

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus)， [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture)， [SetCapture](../mfc/reference/colecontrol-class.md#setcapture)， [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc)， [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

在無視窗控制項中，您應一律使用 `COleControl` 成員函式，而不要使用對應的 `CWnd` 成員函式，或其相關的 Win32 API 函式。

您可能想將無視窗控制項做為 OLE 拖放作業的目標。 通常這會需要將控制項的視窗登錄為置放目標。 由於控制項沒有自己的視窗，因此容器會使用其視窗做為置放目標。 控制項會提供 `IDropTarget` 介面的實作，讓容器能夠在適當時委派呼叫。 若要公開此容器的介面，覆寫[colecontrol:: Getwindowlessdroptarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget)。 例如: 

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項：最佳化](../mfc/mfc-activex-controls-optimization.md)

---
title: MFC ActiveX 控制項：最佳化
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615393"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控制項：最佳化

本文說明您可以用來優化 ActiveX 控制項以獲得更佳效能的技術。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

這些主題會[關閉 [當可見時啟動] 選項](turning-off-the-activate-when-visible-option.md)，並[提供滑鼠互動，而非](providing-mouse-interaction-while-inactive.md)作用中的則會討論不會在啟用之前建立視窗的控制項。 [提供無視窗啟用](providing-windowless-activation.md)的主題會討論永遠不會建立視窗的控制項，即使已啟動也是如此。

Windows 對 OLE 物件有兩大缺點：它們會防止物件在使用中時變成透明或非矩形，而且它們會在具現化和顯示控制項時增加大量的負荷。 通常，建立視窗會耗用控制項建立時間的60%。 使用單一共用的視窗（通常是容器的）和一些分派程式碼，控制項會收到相同的視窗服務，通常不會遺失效能。 有一個視窗大部分是物件不必要的額外負荷。

當您的控制項在某些容器中使用時，某些優化不一定會改善效能。 例如，1996之前發行的容器不支援無視窗啟用，因此，執行這項功能將無法在較舊的容器中提供優勢。 不過，幾乎每個容器都支援持續性，因此優化控制項的持續性程式碼可能會改善其在任何容器中的效能。 如果您的控制項特別適用于某個特定類型的容器，您可能會想要調查該容器支援哪些優化。 不過，一般情況下，您應該嘗試實作為您的特定控制項所適用的多種技術，以確保您的控制項在各種容器中也能執行。

您可以在 [[控制項設定](reference/control-settings-mfc-activex-control-wizard.md)] 頁面上，透過[MFC ActiveX 控制項 Wizard](reference/mfc-activex-control-wizard.md)來執行許多優化。

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控制項嚮導 OLE 優化選項

|MFC ActiveX 控制項 Wizard 中的控制設定|動作|更多資訊|
|-------------------------------------------------------|------------|----------------------|
|**可見時啟動**核取方塊|Clear|[關閉 [當可見時啟動] 選項](turning-off-the-activate-when-visible-option.md)|
|[**無視窗啟用**] 核取方塊|選取|[提供無視窗啟用](providing-windowless-activation.md)|
|[**未裁剪裝置內容**] 核取方塊|選取|[使用未裁剪的裝置內容](using-an-unclipped-device-context.md)|
|[**閃爍-免費**啟動] 核取方塊|選取|[提供 Flicker-Free 啟用](providing-flicker-free-activation.md)|
|非作用中核取方塊**時的滑鼠指標通知**|選取|[非現用時提供滑鼠互動](providing-mouse-interaction-while-inactive.md)|
|**優化的繪圖程式碼**核取方塊|選取|[最佳化控制項繪圖](optimizing-control-drawing.md)|

如需有關執行這些優化之成員函式的詳細資訊，請參閱[COleControl](reference/colecontrol-class.md)。

如需詳細資訊，請參閱：

- [最佳化持續性和初始化](optimizing-persistence-and-initialization.md)

- [提供無視窗啟用](providing-windowless-activation.md)

- [關閉 [當可見時啟動] 選項](turning-off-the-activate-when-visible-option.md)

- [非現用時提供滑鼠互動](providing-mouse-interaction-while-inactive.md)

- [提供 Flicker-Free 啟用](providing-flicker-free-activation.md)

- [使用未裁剪的裝置內容](using-an-unclipped-device-context.md)

- [最佳化控制項繪圖](optimizing-control-drawing.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)

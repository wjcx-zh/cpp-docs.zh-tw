---
title: MFC ActiveX 控制項： 最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4864e0be8ef49541cc59474bdb24c2ef25840007
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441196"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控制項：最佳化

這篇文章說明您可用來最佳化您的 ActiveX 控制項，以提升效能的技巧。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

主題[開啟關閉可見時啟動選項](../mfc/turning-off-the-activate-when-visible-option.md)並[提供滑鼠互動而非使用中](../mfc/providing-mouse-interaction-while-inactive.md)討論不建立視窗啟動之前的控制項。 本主題[提供無視窗啟用](../mfc/providing-windowless-activation.md)討論，即使在啟用時，永遠不會建立視窗中，控制項。

Windows 具有 OLE 物件的兩個主要缺點： 它們就會防止物件被透明或作用中的非矩形和他們新增至的具現化和控制項顯示的大型的額外負荷。 一般而言，建立視窗的時間控制項的建立時間的 60%。 使用單一共用的視窗 （通常是容器的） 和一些分派的程式碼，控制項就會收到相同的 window 服務，通常不會損失效能。 視窗是大部分物件的不必要額外負荷。

在特定容器中使用您的控制項時，則某些最佳化不一定改善效能。 比方說，1996 年之前發行的容器不支援無視窗啟用，所以實作這項功能將不會提供較舊的容器中的權益。 不過，幾乎每個容器都支援持續性，因此最佳化控制項的持續性程式碼可能會改善其任何容器中的效能。 如果您的控制項特別適合用於容器的一個特定的型別，您可能想要研究容器所支援的這些最佳化。 一般情況下，不過，您應該嘗試實作，如上述許多技巧是適用於您特定的控制項，以確保您的控制項執行以及它可能可以在各式各樣的容器。

您可以實作許多透過這些最佳化[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)上[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面。

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控制項精靈 OLE 最佳化選項

|MFC ActiveX 控制項精靈中的控制項設定|動作|詳細資訊|
|-------------------------------------------------------|------------|----------------------|
|**啟動時可見**核取方塊|清除|[關閉啟動時顯示的選項](../mfc/turning-off-the-activate-when-visible-option.md)|
|**無視窗啟用**核取方塊|選用版|[提供無視窗啟用](../mfc/providing-windowless-activation.md)|
|**裁剪的裝置內容**核取方塊|選用版|[使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)|
|**啟用無閃爍**核取方塊|選用版|[提供 Flicker-Free 啟用](../mfc/providing-flicker-free-activation.md)|
|**將滑鼠指標通知非使用中時**核取方塊|選用版|[非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)|
|**最佳化的繪圖程式碼**核取方塊|選用版|[最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)|

如需實作這些最佳化的成員函式的詳細資訊，請參閱[COleControl](../mfc/reference/colecontrol-class.md)。

如需詳細資訊，請參閱:

- [最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md)

- [提供無視窗啟用](../mfc/providing-windowless-activation.md)

- [關閉啟動時顯示的選項](../mfc/turning-off-the-activate-when-visible-option.md)

- [非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)

- [提供 Flicker-Free 啟用](../mfc/providing-flicker-free-activation.md)

- [使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)

- [最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)


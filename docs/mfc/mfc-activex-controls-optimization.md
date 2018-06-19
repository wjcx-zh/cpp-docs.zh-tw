---
title: MFC ActiveX 控制項： 最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c91f147637b53250f8d373af9950d6205c82d3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355307"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控制項：最佳化
本文說明可用來最佳化您的 ActiveX 控制項，以提升效能的技術。  
  
 主題[開啟關閉可見時啟動選項](../mfc/turning-off-the-activate-when-visible-option.md)和[提供滑鼠互動而非使用中](../mfc/providing-mouse-interaction-while-inactive.md)討論視窗啟動之前，請勿建立的控制項。 本主題[提供無視窗啟用](../mfc/providing-windowless-activation.md)討論絕對不要建立視窗中，即使在啟用時的控制項。  
  
 Windows 有 OLE 物件的兩個主要缺點： 它們會防止物件被透明或矩形作用時，以及它們會增加負擔具現化及顯示控制項。 一般而言，建立視窗的時間將控制項的建立時間的 60%。 使用單一共用的視窗 （通常是容器的） 和一些分派的程式碼，控制會接收相同的視窗服務，而不會損失效能。 視窗是物件大多不必要的負荷。  
  
 某些最佳化不一定會改進效能特定容器中使用您的控制項時。 例如，發行 1996 年之前的容器不支援無視窗啟用，所以實作這項功能將不會提供在較舊的容器。 不過，幾乎每個容器都支援持續性，因此最佳化控制項的持續性程式碼可能會改善其任何容器中的效能。 如果您的控制項特別適用於一種特定的類型的容器中，您可能想要研究容器所支援的這些最佳化。 一般情況下，不過，您應該嘗試實作上述許多技巧是適用於您的特定控制項，以確保您的控制項可能執行以及它可能是各種容器中。  
  
 您可以實作許多透過這些最佳化[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)上[控制設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)頁面。  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控制項精靈 OLE 最佳化選項  
  
|MFC ActiveX 控制項精靈中的控制項設定|動作|詳細資訊|  
|-------------------------------------------------------|------------|----------------------|  
|**可見時啟動**核取方塊|清除|[關閉啟動時顯示的選項](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**無視窗啟用**核取方塊|選用版|[提供無視窗啟用](../mfc/providing-windowless-activation.md)|  
|**裁剪的裝置內容**核取方塊|選用版|[使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)|  
|**閃爍的啟用**核取方塊|選用版|[提供 Flicker-Free 啟用](../mfc/providing-flicker-free-activation.md)|  
|**滑鼠指標告知非現用時**核取方塊|選用版|[非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**最佳化繪製程式碼**核取方塊|選用版|[最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)|  
  
 如需實作這些最佳化的成員函式的詳細資訊，請參閱[COleControl](../mfc/reference/colecontrol-class.md)。 成員函式所使用，例如[無視窗作業](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)和[非作用中的處理函式指標](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)。  
  
 如需詳細資訊，請參閱:  
  
-   [最佳化持續性和初始化](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [提供無視窗啟用](../mfc/providing-windowless-activation.md)  
  
-   [關閉啟動時顯示的選項](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [非現用時提供滑鼠互動](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [提供 Flicker-Free 啟用](../mfc/providing-flicker-free-activation.md)  
  
-   [使用未裁剪的裝置內容](../mfc/using-an-unclipped-device-context.md)  
  
-   [最佳化控制項繪圖](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)


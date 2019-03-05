---
title: ActiveX 控制項容器：從 ActiveX 控制項中處理事件
ms.date: 09/12/2018
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
ms.openlocfilehash: 8087d84d2203e4f910200acdd1b00e58d14f920e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293559"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控制項容器：從 ActiveX 控制項中處理事件

這篇文章說明如何使用 [屬性] 視窗在 ActiveX 控制項容器中安裝 ActiveX 控制項的事件處理常式。 事件處理常式用來接收通知 （控制項） 的特定事件，並執行某些動作以回應。 此通知會呼叫 「 引發 」 事件。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

> [!NOTE]
>  本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

使用 [事件] 按鈕，在 [屬性] 視窗中，您可以在對應可能會發生的事件的 ActiveX 控制項容器應用程式。 此地圖中，稱為 「 事件接收對應 '，建立並維護 Visual c + + 中，當您將事件處理常式新增至控制項容器類別。 每個事件處理常式，事件的對應項目，以實作容器事件處理常式成員函式對應特定的事件。 ActiveX 控制項物件所指定的事件引發時，會呼叫此事件處理常式函式。

如需有關事件接收對應的詳細資訊，請參閱 <<c0> [ 事件接收對應](../mfc/reference/event-sink-maps.md)中*類別庫參考*。

##  <a name="_core_event_handler_modifications_to_the_project"></a> 事件處理常式修改專案

當您使用 [屬性] 視窗新增事件處理常式時，事件接收對應宣告，然後在您的專案中定義。 下列陳述式加入至控制項。CPP 檔案會加入事件處理常式的第一次。 此程式碼會宣告事件接收對應的對話方塊類別 (在此情況下， `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

當您使用 [屬性] 視窗新增事件時，事件對應項目 (`ON_EVENT`) 加入事件接收對應和事件處理常式函式加入至容器的實作 (。CPP) 檔案。

下列範例會宣告事件處理常式，呼叫`OnClickInCircCtrl`，Circ 控制項`ClickIn`事件：

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外，下列範本會加入至`CContainerDlg`類別實作 (。事件處理常式成員函式的 CPP) 檔案：

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

如需有關事件接收器巨集的詳細資訊，請參閱[事件接收對應](../mfc/reference/event-sink-maps.md)中*類別庫參考*。

#### <a name="to-create-an-event-handler-function"></a>若要建立的事件處理常式函式

1. 從 [類別] 檢視中，選取包含 ActiveX 控制項的對話方塊類別。 此範例中，使用`CContainerDlg`。

1. 在 屬性 視窗中，按一下**事件** 按鈕。

1. 在 [屬性] 視窗中，選取內嵌 ActiveX 控制項的控制項 ID。 此範例中，使用`IDC_CIRCCTRL1`。

   [屬性] 視窗會顯示一份可以內嵌 ActiveX 控制項所引發的事件。 已經以粗體顯示的任何成員函式具有指派給它的處理常式函式。

1. 選取您想要處理的對話方塊類別的事件。 此範例中，選取**按一下**。

1. 從下拉式清單方塊的右邊，選取**\<新增 > ClickCircctrl1**。

1. 按兩下新的處理常式函式，可前往 事件處理常式程式碼，在實作中的 類別檢視 (。CPP) 檔案的`CContainerDlg`。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)

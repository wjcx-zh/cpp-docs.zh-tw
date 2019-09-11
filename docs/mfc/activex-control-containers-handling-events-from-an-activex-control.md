---
title: ActiveX 控制項容器：處理來自 ActiveX 控制項的事件
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
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907765"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控制項容器：處理來自 ActiveX 控制項的事件

本文討論如何使用 [**屬性**] 視窗（在**類別檢視**中），在 activex 控制項容器中安裝 activex 控制項的事件處理常式。 事件處理常式是用來接收特定事件的通知（來自控制項），並在回應中執行某些動作。 此通知稱為「引發」事件。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

> [!NOTE]
>  本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

使用 [**屬性**] 視窗中的 [事件] 按鈕（在**類別檢視**中），您可以建立可在 ActiveX 控制項容器應用程式中發生之事件的對應。 當您將事件處理常式加入至控制項容器類別時，視覺效果C++會建立並維護這個對應（稱為「事件接收對應」）。 每個事件處理常式（以事件對應專案來執行）都會將特定事件對應至容器事件處理常式成員函式。 當 ActiveX 控制項物件引發指定的事件時，就會呼叫這個事件處理常式函式。

如需事件接收對應的詳細資訊，請參閱*類別庫參考*中的[事件接收器對應](../mfc/reference/event-sink-maps.md)。

##  <a name="_core_event_handler_modifications_to_the_project"></a>專案的事件處理常式修改

當您使用 [**屬性**] 視窗加入事件處理常式時，系統會在您的專案中宣告和定義事件接收對應。 下列語句會加入至控制項。當第一次加入事件處理常式時的 CPP 檔案。 此程式碼會宣告對話方塊類別的事件接收對應（在此案例`CContainerDlg`中為）：

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

當您使用 [**屬性**] 視窗加入事件時，會將事件對應`ON_EVENT`專案（）新增至事件接收對應，並將事件處理常式函式新增至容器的執行（。CPP）檔案。

下列範例會針對 Circ 控制項的`OnClickInCircCtrl` `ClickIn`事件，宣告名為的事件處理常式：

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外，下列範本會加入至`CContainerDlg`類別執行（。CPP）檔案做為事件處理常式成員函式：

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

如需事件接收器宏的詳細資訊，請參閱*類別庫參考*中的[事件接收器對應](../mfc/reference/event-sink-maps.md)。

#### <a name="to-create-an-event-handler-function"></a>若要建立事件處理常式函數

1. 從 [類別檢視] 中，選取包含 ActiveX 控制項的對話方塊類別。 針對此範例，請`CContainerDlg`使用。

1. 在 [屬性] 視窗中，按一下 [事件] 按鈕。

1. 在 [**屬性**] 視窗中，選取內嵌 ActiveX 控制項的控制項 ID。 針對此範例，請`IDC_CIRCCTRL1`使用。

   [**屬性**] 視窗會顯示內嵌 ActiveX 控制項可以引發的事件清單。 以粗體顯示的任何成員函式已經有指派給它的處理常式函式。

1. 選取您想要對話類別處理的事件。 在此範例中，選取 [**按一下**]。

1. 從下拉式清單方塊的右邊，選取 **\<新增 > ClickCircctrl1** 。

1. 按兩下 類別檢視中的新處理常式函式，跳至執行中的事件處理常式程式碼（。的`CContainerDlg`.cpp）檔案。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)

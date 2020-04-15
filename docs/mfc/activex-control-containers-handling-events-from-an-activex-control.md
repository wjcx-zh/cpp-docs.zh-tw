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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367944"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX 控制項容器：從 ActiveX 控制項中處理事件

本文討論使用**屬性**視窗(**類別檢視**中) 在 ActiveX 控制件容器中為 ActiveX 控制套件安裝事件處理程式。 事件處理程式用於接收某些事件的通知(來自控件),並在回應中執行某些操作。 此通知稱為「觸發」事件。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

> [!NOTE]
> 本文使用對話架構的 ActiveX 控制項容器專案 (名為 Container) 和內嵌控制項 (名為 Circ) 做為程序和程式碼的範例。

使用 **「屬性**」視窗中的事件按鈕(**在類檢視中**),可以創建 ActiveX 控制件容器應用程式中可能發生的事件對應。 此映射稱為"事件接收器映射",由 Visual C++在將事件處理程式添加到控制項容器類時創建和維護。 每個事件處理程式(使用事件映射條目實現)將特定事件映射到容器事件處理程序成員函數。 當 ActiveX 控制件物件觸發指定事件時,將調用此事件處理程式函數。

有關事件接收器對應的詳細資訊,請參考*類別庫參考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>事件處理程式對專案的修改

使用 **「屬性」** 視窗添加事件處理程式時,將聲明和在專案中定義事件接收器映射。 以下語句將添加到控制項中。首次添加事件處理程式時,CPP 檔。 此程式碼聲明對話方塊類別的事件接收器映射(在本`CContainerDlg`例中為 ):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

當您使用 **「屬性」** 視窗添加事件時,事件映射項目`ON_EVENT`( ) 將添加到事件接收器映射中,並將事件處理程式函數添加到容器的實現 ()。CPP)檔。

以下範例宣告 Circ`OnClickInCircCtrl``ClickIn`控制件 事件的事件處理程式,稱為 ,該處理程式:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

此外,以下範本將添加到`CContainerDlg`類實現 (。事件處理常式成員函數的 CPP 檔案:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

有關事件接收器巨集的詳細資訊,請參閱*類別庫參考*中的[事件接收器映射](../mfc/reference/event-sink-maps.md)。

#### <a name="to-create-an-event-handler-function"></a>建立事件處理常式函數

1. 從類檢視中,選擇包含 ActiveX 控制件的對話方塊類。 這個範例中, 請`CContainerDlg`使用 。

1. 在 [屬性]**** 視窗中，按一下 [事件]**** 按鈕。

1. 在 **「屬性」** 視窗中,選擇嵌入的 ActiveX 控制件的控制 ID。 這個範例中, 請`IDC_CIRCCTRL1`使用 。

   屬性 **「** 視窗顯示可由嵌入的 ActiveX 控件觸發的事件清單。 以粗體顯示的任何成員函數都已為其分配了處理程式函數。

1. 選擇要處理對話方塊類的事件。 這個選項, 選擇**按下**。

1. 從右方的下拉清單框中,選擇「**\<新增> ClickCircctrl1**。

1. 按兩下類檢視的新處理程式函數以跳轉到實現中的事件處理程式代碼 (。的 CPP)`CContainerDlg`檔案。

## <a name="see-also"></a>另請參閱

[ActiveX 控制項容器](../mfc/activex-control-containers.md)

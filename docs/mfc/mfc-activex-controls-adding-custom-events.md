---
title: MFC ActiveX 控制項：加入自訂事件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364722"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控制項：加入自訂事件

自定義事件與股票事件不同,因為它們不會由類`COleControl`自動觸發。 自定義事件將由控制項開發人員確定的特定操作識別為事件。 自定義事件的事件映射條目由EVENT_CUSTOM宏表示。 以下部分為使用 ActiveX 控制精靈建立的 ActiveX 控制件專案實現自訂事件。

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>使用新增事件精靈新增自訂事件

以下過程添加了特定的自定義事件 ClickIn。 可以使用此過程添加其他自定義事件。 將自訂事件名稱及其參數替換為 ClickIn 事件名稱和參數。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>使用「新增事件精靈」新增「點擊」自訂事件

1. 載入控制項專案。

1. 在**類檢視中**,右鍵單擊 ActiveX 控件類以打開快捷功能表。

1. 在快捷選單中,按一下「**添加」,** 然後按下「**添加事件**」。

   這將打開「添加事件嚮導」。

1. 在 **「事件名稱**」 框中,首先選擇任何現有事件,然後按下 **「自訂**單選」按鈕,然後鍵入*ClickIn*。

1. 在 **「內部名稱**」框中,鍵入事件觸發函數的名稱。 在此範例中,請使用新增事件精靈( )`FireClickIn`提供的預設值。

1. 使用**參數名稱**和**參數類型**控制項添加一個參數,稱為*xCoord(* 類型*OLE_XPOS_PIXELS*)。

1. 添加第二個參數,稱為*yCoord(**類型OLE_YPOS_PIXELS*)。

1. 按下 **「完成」** 以建立事件。

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>為自訂事件新增事件精靈變更

新增自訂事件時,「新增事件精靈」會更改控制項類別 。H。CPP 與 。IDL 檔。 以下代碼示例特定於 ClickIn 事件。

以下行將添加到標頭 (。H) 控制類別的檔案:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此代碼聲明一個內聯函數,`FireClickIn`稱為[COleControl::FireEvent,](../mfc/reference/colecontrol-class.md#fireevent)包含使用添加事件嚮導定義的 ClickIn 事件和參數。

此外,下一行將添加到位於實現 (的控制件的事件映射中。控制類的 CPP 檔案:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此代碼將事件 ClickIn 映射到內聯`FireClickIn`函數 ,傳遞使用添加事件嚮導定義的參數。

最後,將以下行添加到控制項的 。IDL 檔案:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

此行為 ClickIn 事件分配一個特定的 ID 號,該 ID 號取自事件在「添加事件嚮導」事件清單中的位置。 事件清單中的項目允許容器預測事件。 例如,它可能提供觸發事件時要執行的處理程式代碼。

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>呼叫火

現在,您已經使用"添加事件嚮導"添加了 ClickIn 自定義事件,您必須決定何時觸發此事件。 執行此操作時調用`FireClickIn`相應的操作。 對於此討論,當用戶單擊圓形`InCircle`或橢`WM_LBUTTONDOWN`圓 區域時,控件使用消息處理程序內的函數觸發 ClickIn 事件。 以下過程添加`WM_LBUTTONDOWN`處理程式。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>使用「新增事件精靈」新增訊息處理程式

1. 載入控制項專案。

1. 在**類檢視中**,選擇 ActiveX 控件類。

1. 在 **「屬性」** 視窗中,您將看到一個由 ActiveX 控件可以處理的消息清單。 以粗體顯示的任何消息都已為其分配了處理程式函數。

1. 選擇要處理的消息。 這個範例中,`WM_LBUTTONDOWN`選擇 。

1. 從右方的下拉清單框中,選擇**\<「新增> OnLButtonDown**。

1. 按兩下**類檢視中**的新處理程式函數以跳轉到實現中的消息處理程式代碼 (。ActiveX 控制項的 CPP)檔。

每次在控制視窗中按一下滑`InCircle`鼠 左鍵時,以下代碼示例都會調用該函數。 此範例可以在`WM_LBUTTONDOWN`處理程式函數 中`OnLButtonDown`找到, 在 Circ[範例](../overview/visual-cpp-samples.md)摘要中找到。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> 當添加事件嚮導為滑鼠按鈕操作創建消息處理程式時,將自動添加對基類的同一消息處理程序的調用。 不要刪除此呼叫。 如果控件使用任何庫存滑鼠消息,則必須調用基類中的消息處理程式以確保正確處理滑鼠捕獲。

在下面的示例中,僅當單擊發生在控件內的圓形或橢圓區域中時,事件才會觸發。 要實現此行為,可以將`InCircle`函數放在控件的實現中 (。CPP) 檔案:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

您還需要將`InCircle`函數的以下聲明添加到控制項的標頭 (。H) 檔案:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>具有股票名稱的自訂事件

您可以創建與股票事件同名的自定義事件,但不能在同一控件中實現這兩個事件。 例如,您可能希望創建名為 Click 的自定義事件,該自定義事件在股票事件 Click 通常會觸發時不會觸發。 然後,您可以隨時通過調用其觸發函數觸發 Click 事件。

以下過程添加自定義 Click 事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>新增使用股票事件名稱的自訂事件

1. 載入控制項專案。

1. 在**類檢視中**,右鍵單擊 ActiveX 控件類以打開快捷功能表。

1. 在快捷選單中,按一下「**添加」,** 然後按下「**添加事件**」。

   這將打開「添加事件嚮導」。

1. 在**事件名稱**下拉清單中,選擇股票事件名稱。 這個選項, 選擇**按下**。

1. 對於**事件類型**,選擇 **「自訂**」。

1. 按下 **「完成」** 以建立事件。

1. 在`FireClick`代碼的適當位置呼叫。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

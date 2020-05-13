---
title: MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364693"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項

股票事件與自定義事件不同,因為它們由[COleControl](../mfc/reference/colecontrol-class.md)類自動觸發。 `COleControl`包含預定義的成員函數,這些函數觸發由常見操作引起的事件。 通過實現`COleControl`的某些常見操作包括對控制項的單次單擊和按兩下、鍵盤事件以及更改滑鼠按鈕的狀態。 股票事件的事件映射條目始終前面有EVENT_STOCK首碼。

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>新增事件精靈支援的股票事件

該`COleControl`類提供十個股票事件,列在下表中。 您可以使用[「新增事件精靈](../ide/add-event-wizard.md)」在控制項中指定所需的事件。

### <a name="stock-events"></a>股票事件

|事件|點火功能|註解|
|-----------|---------------------|--------------|
|按一下 |**空火點擊( )**|當控制器擷取滑鼠時觸發,收到任何**BUTTONUP(** 左、中或右)消息,並在控制項上釋放按鈕。 庫存滑鼠向下和滑鼠Up事件在此事件之前發生。<br /><br /> 事件地圖項目: **EVENT_STOCK_CLICK( )**|
|DblClick|**空火點點擊( )**|類似於單擊,但在收到**BUTTONDBLCLK**消息時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_DBLCLICK( )**|
|錯誤|**空火錯誤(SCODE***碼***, LPCSTR,** `lpszDescription` **UINT**`nHelpID`= 0 **)**        |當在方法調用或屬性訪問範圍之外的 ActiveX 控件中發生錯誤時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**空火鍵下(短**`nChar`**, 短**`nShiftState`**)**      |收到`WM_SYSKEYDOWN``WM_KEYDOWN`或消息時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_KEYDOWN( )**|
|鍵新聞|**空火鍵新聞(短**<strong>\*</strong>`pnChar`**)**    |收到`WM_CHAR`消息時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**空火鑰匙(短**`nChar`**,短**`nShiftState`**)**      |收到`WM_SYSKEYUP``WM_KEYUP`或消息時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_KEYUP( )**|
|滑鼠向下|**空火滑鼠向下(短**`nButton`**, 短**`nShiftState`**, 浮點***x,* **浮點***y)* ** **          |如果收到任何**BUTTONDOWN(** 左、中或右),則觸發。 在觸發此事件之前,將立即捕獲滑鼠。<br /><br /> 事件地圖項目: **EVENT_STOCK_MOUSEDOWN( )**|
|滑鼠移動|**空火滑鼠移動(短**`nButton`**,短**`nShiftState`**,浮點***x,***浮點***y)* ** **          |收到WM_MOUSEMOVE消息時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_MOUSEMOVE ( )**|
|滑鼠向上|**空火滑鼠(短**`nButton`**,短**`nShiftState`**,浮點***x,***浮點***y)* ** **          |如果收到任何**BUTTONUP(** 左、中或右),則觸發。 在觸發此事件之前釋放滑鼠捕獲。<br /><br /> 事件地圖項目: **EVENT_STOCK_MOUSEUP( )**|
|就緒狀態變更|**空火準備狀態轉換( )**|當控件由於接收的數據量而轉換到下一個就緒狀態時觸發。<br /><br /> 事件地圖項目: **EVENT_STOCK_READYSTATECHANGE( )**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>使用新增事件精靈加入股票事件

新增股票事件所需的工作比新增自訂事件少,因為實際事件的觸發由基類自動處理`COleControl`。 以下過程將庫存事件添加到使用[MFC ActiveX 控制嚮導](../mfc/reference/mfc-activex-control-wizard.md)開發的控制項。 當按鍵且控件處於活動狀態時,該事件稱為 KeyPress。 此過程還可用於添加其他庫存事件。 將所選股票事件名稱替換為 KeyPress。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>使用「新增事件精靈」新增 KeyPress 股票事件

1. 載入控制項專案。

1. 在類檢視中,右鍵單擊 ActiveX 控件類以打開快捷功能表。

1. 在快捷選單中,按一下「**添加」,** 然後按下「**添加事件**」。

   這將打開「添加事件嚮導」。

1. 在 **「事件名稱**」 下拉清單`KeyPress`中, 選擇 。

1. 按一下 [完成] 。

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>新增股票事件的事件精靈變更

由於股票事件由控件的基類處理,因此添加事件嚮導不會以任何方式更改類聲明。 它將事件添加到控制項的事件映射,並在其中進行條目。IDL 檔。 下一行將添加到位於控制項類實現 (的控制項的事件映射中。CPP) 檔案:

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

當收到WM_CHAR消息且控件處於活動狀態時,添加此代碼將觸發 KeyPress 事件。 KeyPress 事件可以透過在控制代碼中呼叫其觸發函數(例如`FireKeyPress`), 在其他時間觸發。

新增事件精靈將以下代碼行到控制項的 。IDL 檔案:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

此行將 KeyPress 事件與其標準調度 ID 關聯,並允許容器預測 KeyPress 事件。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

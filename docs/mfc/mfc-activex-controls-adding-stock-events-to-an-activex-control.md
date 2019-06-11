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
ms.openlocfilehash: 9f6f3c63f0436296791df428c704bce96eca3ec0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392722"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項

內建事件與不同的自訂事件類別會自動引發[COleControl](../mfc/reference/colecontrol-class.md)。 `COleControl` 包含引發事件所產生的一般動作的預先定義的成員函式。 一些常見的動作，藉由將`COleControl`納入單一-和按兩下-clicks 控制項、 鍵盤事件和變更滑鼠按鍵的狀態。 事件對應股票 EVENT_STOCK 前置詞一律置於事件的項目。

##  <a name="_core_stock_events_supported_by_classwizard"></a> 內建支援的事件加入事件精靈

`COleControl`類別會提供十個內建的事件，如下表所示。 您可以指定您想要在控制項中使用的事件[加入事件精靈](../ide/add-event-wizard.md)。

### <a name="stock-events"></a>內建事件

|Event - 事件|引發函式|註解|
|-----------|---------------------|--------------|
|按一下|**void FireClick( )**|發生於控制項捕捉滑鼠，任何**BUTTONUP**收到 （左、 置中 或右） 的訊息，並在控制項上方且放開按鈕。 MouseDown 股票圖和 MouseUp 事件會發生此事件之前。<br /><br /> 事件對應項目：**EVENT_STOCK_CLICK( )**|
|DblClick|**void FireDblClick( )**|按一下 類似但引發的時機**BUTTONDBLCLK**接收訊息。<br /><br /> 事件對應項目：**EVENT_STOCK_DBLCLICK( )**|
|錯誤|**void FireError( SCODE**  *scode* **, LPCSTR**  `lpszDescription` **, UINT**  `nHelpID`  **= 0 )**|當您的 ActiveX 控制項之外的方法呼叫或屬性存取範圍內發生錯誤時引發。<br /><br /> 事件對應項目：**EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**void FireKeyDown( short**  `nChar` **, short**  `nShiftState`  **)**|引發的時機`WM_SYSKEYDOWN`或`WM_KEYDOWN`接收訊息。<br /><br /> 事件對應項目：**EVENT_STOCK_KEYDOWN( )**|
|KeyPress|**void FireKeyPress( short** <strong>\*</strong>  `pnChar`  **)**|時引發`WM_CHAR`接收訊息。<br /><br /> 事件對應項目：**EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**void FireKeyUp (簡短**`nChar` **，short**`nShiftState` **)**|引發的時機`WM_SYSKEYUP`或`WM_KEYUP`接收訊息。<br /><br /> 事件對應項目：**EVENT_STOCK_KEYUP( )**|
|MouseDown|**void FireMouseDown (簡短**`nButton` **，short** `nShiftState` **，float** *x* **，float** *y* **)**|引發如果有的話**BUTTONDOWN**收到 （左邊、 中間或右邊）。 將滑鼠擷取之前引發此事件。<br /><br /> 事件對應項目：**EVENT_STOCK_MOUSEDOWN( )**|
|MouseMove|**void FireMouseMove (簡短**`nButton` **，short** `nShiftState` **，float** *x* **，float** *y* **)**|當收到 WM_MOUSEMOVE 訊息時引發。<br /><br /> 事件對應項目：**EVENT_STOCK_MOUSEMOVE( )**|
|MouseUp|**void FireMouseUp (簡短**`nButton` **，short** `nShiftState` **，float** *x* **，float** *y* **)**|引發如果有的話**BUTTONUP**收到 （左邊、 中間或右邊）。 此事件引發之前，會釋出滑鼠捕捉。<br /><br /> 事件對應項目：**EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|當控制項轉換成下一個就緒狀態，因為收到的資料量時引發。<br /><br /> 事件對應項目：**EVENT_STOCK_READYSTATECHANGE( )**|

##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 新增使用內建事件加入事件精靈

新增內建事件需要較少的工作比新增自訂事件，因為實際事件的引發基底類別，會自動處理`COleControl`。 下列程序會將內建事件加入至使用所開發的控制項[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。 當按下按鍵，而且控制項是作用中時，就會引發事件，稱為 KeyPress。 此程序也可用來新增其他內建的事件。 使用按鍵動作選取的內建事件名稱。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>若要新增該 KeyPress 內建事件加入事件精靈

1. 載入控制項專案。

1. 類別檢視 中以滑鼠右鍵按一下您的 ActiveX 控制項類別，若要開啟快顯功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**新增事件**。

   這會開啟 [新增事件精靈]。

1. 在 **事件名稱**下拉式清單中，選取`KeyPress`。

1. 按一下 [ **完成**]。

##  <a name="_core_classwizard_changes_for_stock_events"></a> 針對內建事件加入事件精靈的變更

因為內建事件會由控制項的基底類別，加入事件精靈不會變更您的類別宣告，以任何方式。 它將事件加入至控制項的事件對應並且中的項目其。IDL 檔案。 下面這一行加入至控制項的事件對應，位於控制項類別實作 (。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

加入此程式碼，就會引發 KeyPress 事件時收到 WM_CHAR 訊息，而且控制項是使用中。 可以在其他時間引發 KeyPress 事件，藉由呼叫其引發函式 (例如`FireKeyPress`) 從控制項程式碼中。

加入事件精靈會將下列程式碼行加入至控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

這行關聯其標準的分派識別碼的按鍵事件，並可讓容器預期按鍵事件。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

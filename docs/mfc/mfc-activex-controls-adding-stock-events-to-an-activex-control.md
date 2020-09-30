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
ms.openlocfilehash: e63e63b914b9db64139b9b81a2c749a78ac4a58f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503860"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項

股票事件與自訂事件不同之處在于，類別 [COleControl](reference/colecontrol-class.md)會自動引發這些事件。 `COleControl` 包含預先定義的成員函式，這些函式會引發常見動作所產生的事件。 由執行的一些常見動作 `COleControl` 包括在控制項上按一下單一和按兩下、鍵盤事件，以及滑鼠按鍵的狀態變更。 內建事件的事件對應專案的前面一律會加上 EVENT_STOCK 前置詞。

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a> Add Event Wizard 支援的存貨事件

此 `COleControl` 類別提供10個內建事件，如下表所列。 您可以使用 [ [加入事件嚮導]](../ide/adding-an-event-visual-cpp.md#add-event-wizard)，在控制項中指定您想要的事件。

### <a name="stock-events"></a>存貨活動

|事件|引發函式|註解|
|-----------|---------------------|--------------|
|按一下|**void FireClick ( ) **|當控制項捕捉到滑鼠、任何 **BUTTONUP** (left、中間或右) 訊息時引發，而且按鈕會在控制項上放開。 Stock MouseDown 和 MouseUp 事件發生在此事件之前。<br /><br /> 事件對應專案： **EVENT_STOCK_CLICK ( ) **|
|DblClick|**void FireDblClick ( ) **|類似于按一下，但在收到 **BUTTONDBLCLK** 訊息時引發。<br /><br /> 事件對應專案： **EVENT_STOCK_DBLCLICK ( ) **|
|Error|**void FireError ( SCODE***SCODE* **、LPCSTR** `lpszDescription` **、UINT** `nHelpID` **= 0 ) **        |在方法呼叫或屬性存取範圍之外的 ActiveX 控制項中發生錯誤時引發。<br /><br /> 事件對應專案： **EVENT_STOCK_ERROREVENT ( ) **|
|KeyDown|**Void FireKeyDown ( short** `nChar`**、short** `nShiftState`**) **      |當 `WM_SYSKEYDOWN` 收到或訊息時引發 `WM_KEYDOWN` 。<br /><br /> 事件對應專案： **EVENT_STOCK_KEYDOWN ( ) **|
|KeyPress|**Void FireKeyPress ( short** <strong>\*</strong> `pnChar`**) **    |在 `WM_CHAR` 收到訊息時引發。<br /><br /> 事件對應專案： **EVENT_STOCK_KEYPRESS ( ) **|
|KeyUp|**Void FireKeyUp ( short** `nChar`**、short** `nShiftState`**) **      |當 `WM_SYSKEYUP` 收到或訊息時引發 `WM_KEYUP` 。<br /><br /> 事件對應專案： **EVENT_STOCK_KEYUP ( ) **|
|MouseDown|**Void FireMouseDown ( short** `nButton`**、short** `nShiftState`**，float***x* **，float***y* **) **          |如果收到任何 **BUTTONDOWN** (left、中間或右) ，就會引發。 在引發此事件之前，會立即捕捉滑鼠。<br /><br /> 事件對應專案： **EVENT_STOCK_MOUSEDOWN ( ) **|
|MouseMove|**Void FireMouseMove ( short** `nButton`**、short** `nShiftState`**，float***x* **，float***y* **) **          |收到 WM_MOUSEMOVE 訊息時引發。<br /><br /> 事件對應專案： **EVENT_STOCK_MOUSEMOVE ( ) **|
|MouseUp|**Void FireMouseUp ( short** `nButton`**、short** `nShiftState`**，float***x* **，float***y* **) **          |如果收到任何 **BUTTONUP** (left、中間或右) ，就會引發。 在引發此事件之前，會釋放滑鼠捕捉。<br /><br /> 事件對應專案： **EVENT_STOCK_MOUSEUP ( ) **|
|ReadyStateChange|**void FireReadyStateChange ( ) **|當控制項因為收到的資料量而轉換至下一個就緒狀態時，就會引發。<br /><br /> 事件對應專案： **EVENT_STOCK_READYSTATECHANGE ( ) **|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a> 使用 Add Event Wizard 新增股票活動

新增內建事件需要較少的工作，因為引發實際事件是由基類（base class）自動處理 `COleControl` 。 下列程式會將內建事件新增至使用 [MFC ActiveX 控制項 Wizard](reference/mfc-activex-control-wizard.md)開發的控制項。 當按下按鍵且控制項為作用中時，就會引發稱為「按鍵」的事件。 此程式也可以用來新增其他內建事件。 將選取的內建事件名稱替換成按鍵。

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>若要使用 Add Event Wizard 新增按鍵活動

1. 載入控制項專案。

1. 在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別以開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入事件**]。

   這會開啟 [加入事件] Wizard。

1. 在 [ **事件名稱** ] 下拉式清單中，選取 `KeyPress` 。

1. 按一下 [完成] 。

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a> 新增內建事件的事件嚮導變更

因為內建事件是由控制項的基類處理，所以 [加入事件] Wizard 不會以任何方式變更您的類別宣告。 它會將事件新增至控制項的事件對應，並在其中建立專案。IDL 檔案。 下一行會加入控制項的事件對應中，位於控制項類別的 [執行 (] 中。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

加入此程式碼會在收到 WM_CHAR 訊息且控制項為使用中時引發按鍵事件。 您可以呼叫引發函式，在其他時間引發 KeyPress 事件 (例如， `FireKeyPress` 從控制項程式碼內) 。

Add Event Wizard 會將下列程式碼新增至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

這一行會將按鍵事件與標準分派識別碼產生關聯，並允許容器預測按鍵事件。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)

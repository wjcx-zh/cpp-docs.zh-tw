---
title: MFC ActiveX 控制項： 加入至 ActiveX 控制項的內建事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41445015f30eb953675f763652fb85ef3eeb857a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930783"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項
內建事件與不同的自訂事件類別會自動引發[COleControl](../mfc/reference/colecontrol-class.md)。 `COleControl` 包含引發事件，從一般動作所產生的預先定義的成員函式。 某些常見的動作由實作`COleControl`併入單一-並按兩下-clicks 上控制、 鍵盤事件和變更滑鼠按鈕的狀態。 事件對應內建事件一律會置於 EVENT_STOCK 前置詞的項目。  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> 內建支援的事件加入事件精靈  
 `COleControl`類別會提供十個內建的事件，如下表所示。 您可以指定您想要在控制項中使用的事件[加入事件精靈](../ide/add-event-wizard.md)。  
  
### <a name="stock-events"></a>內建事件  
  
|Event - 事件|引發的函式|註解|  
|-----------|---------------------|--------------|  
|按一下|**void FireClick （)**|發生於控制項捕捉滑鼠，任何**BUTTONUP**收到 （左、 置中 或右） 的訊息，且控制項上方且放開按鈕。 MouseDown 股票圖和 MouseUp 事件會發生此事件之前。<br /><br /> 事件對應項目： **EVENT_STOCK_CLICK （)**|  
|DblClick|**void FireDblClick （)**|按一下類似但引發的時機**BUTTONDBLCLK**接收訊息。<br /><br /> 事件對應項目： **EVENT_STOCK_DBLCLICK （)**|  
|錯誤|**void FireError (SCODE***scode* **，LPCSTR** `lpszDescription` **，UINT**`nHelpID`**= 0)** |在超出範圍的方法呼叫或屬性存取 ActiveX 控制項中發生錯誤時引發。<br /><br /> 事件對應項目： **EVENT_STOCK_ERROREVENT （)**|  
|KeyDown|**void FireKeyDown (簡短**`nChar` **，short**`nShiftState`**)** |引發的時機`WM_SYSKEYDOWN`或`WM_KEYDOWN`接收訊息。<br /><br /> 事件對應項目： **EVENT_STOCK_KEYDOWN （)**|  
|KeyPress|**void FireKeyPress (簡短\***`pnChar`**)** |引發的時機`WM_CHAR`接收訊息。<br /><br /> 事件對應項目： **EVENT_STOCK_KEYPRESS （)**|  
|KeyUp|**void FireKeyUp (簡短**`nChar` **，short**`nShiftState`**)** |引發的時機`WM_SYSKEYUP`或`WM_KEYUP`接收訊息。<br /><br /> 事件對應項目： **EVENT_STOCK_KEYUP （)**|  
|MouseDown|**void FireMouseDown (簡短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |如果有任何引發**BUTTONDOWN**收到 （左、 置中或右）。 將滑鼠擷取之前引發此事件。<br /><br /> 事件對應項目： **EVENT_STOCK_MOUSEDOWN （)**|  
|MouseMove|**void FireMouseMove (簡短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |當收到 WM_MOUSEMOVE 訊息時引發。<br /><br /> 事件對應項目： **EVENT_STOCK_MOUSEMOVE （)**|  
|MouseUp|**void FireMouseUp (簡短**`nButton` **，short** `nShiftState` **，float***x* **，float** *y***)** |如果有任何引發**BUTTONUP**收到 （左、 置中或右）。 引發此事件之前，會釋放滑鼠捕捉。<br /><br /> 事件對應項目： **EVENT_STOCK_MOUSEUP （)**|  
|ReadyStateChange|**void FireReadyStateChange （)**|發生於控制項會轉換到下一步的就緒狀態，因為收到的資料量。<br /><br /> 事件對應項目： **EVENT_STOCK_READYSTATECHANGE （)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 加入使用內建事件加入事件精靈  
 新增內建事件需要比加入自訂事件，因為實際事件的引發基底類別，會自動處理較少工作`COleControl`。 下列程序會將內建事件加入至控制項利用開發[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。 ，呼叫按鍵動作，就會引發事件時按下按鍵且控制項為使用中。 此程序也可用來新增其他內建事件。 替代 KeyPress 選取內建的事件名稱。  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>若要加入使用加入事件精靈 KeyPress 內建事件  
  
1.  載入控制項專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別若要開啟快顯功能表。  
  
3.  從捷徑功能表，按一下 **新增**，然後按一下 **加入事件**。  
  
     這會開啟 加入事件精靈。  
  
4.  在**事件名稱**下拉式清單中，選取`KeyPress`。  
  
5.  按一下 [ **完成**]。  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> 針對內建事件加入事件精靈變更  
 內建事件由控制項的基底類別處理，因為加入事件精靈不會變更您的類別宣告，以任何方式。 它將事件加入至控制項的事件對應，並在其。IDL 檔案。 下列這一行加入至控制項的事件對應，位於控制項類別實作 (。CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 加入這個程式碼就會引發 KeyPress 事件時收到 WM_CHAR 訊息，而控制項則使用中。 KeyPress 事件可以在其他時間引發藉由呼叫其引發的函式 (例如， `FireKeyPress`) 從控制項的程式碼中。  
  
 加入事件精靈會將下列程式碼行加入至控制項。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 這一行將 KeyPress 事件與標準分派識別碼產生關聯，並可讓容器預測 KeyPress 事件。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)

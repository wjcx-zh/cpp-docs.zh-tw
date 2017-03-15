---
title: "MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENT__STOCK_ERROR"
  - "EVENT__STOCK_READYSTATECHANGE"
  - "ReadyStateChange"
  - "EVENT__STOCK_MOUSEMOVE"
  - "EVENT__STOCK_MOUSEUP"
  - "EVENT__STOCK_DBLCLICK"
  - "KeyPress"
  - "EVENT__STOCK_KEYDOWN"
  - "EVENT__STOCK"
  - "EVENT__STOCK_MOUSEDOWN"
  - "EVENT__STOCK_KEYPRESS"
  - "EVENT__STOCK_CLICK"
  - "EVENT__STOCK_KEYUP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EVENT_STOCK 前置詞"
  - "EVENT_STOCK_CLICK 事件"
  - "EVENT_STOCK_DBLCLICK 事件"
  - "EVENT_STOCK_ERROREVENT 事件"
  - "EVENT_STOCK_KEYDOWN 事件"
  - "EVENT_STOCK_KEYPRESS 事件"
  - "EVENT_STOCK_KEYPRESS 巨集"
  - "EVENT_STOCK_KEYUP 事件"
  - "EVENT_STOCK_MOUSEDOWN 事件"
  - "EVENT_STOCK_MOUSEMOVE 事件"
  - "EVENT_STOCK_MOUSEUP 事件"
  - "EVENT_STOCK_READYSTATECHANGE 事件"
  - "事件 [C++], 內建"
  - "FireClick 事件"
  - "FireDblClick 事件"
  - "FireError 事件"
  - "FireKeyDown 事件"
  - "FireKeyPress 事件"
  - "FireKeyUp 事件"
  - "FireMouseDown 事件"
  - "FireMouseMove 事件"
  - "FireMouseUp 事件"
  - "KeyPress 事件"
  - "MFC ActiveX 控制項, 事件"
  - "ReadyStateChange 事件"
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控制項：將內建事件加入至 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內建事件與自訂事件不同在於它們是由類別 [COleControl](../mfc/reference/colecontrol-class.md) 自動引發。  `COleControl` 包含預先定義的成員函式，其會因為一般動作而引發事件。  `COleControl` 實作的一些常見的動作包括單一和按兩下控制項、鍵盤事件和滑鼠狀態變更。  內建事件的事件對應項目永遠會在 **EVENT\_STOCK** 前置詞之後。  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> 加入事件精靈支援的內建事件  
 `COleControl` 類別提供十個內建事件，列在下表中。  您可以使用 [加入事件精靈](../ide/add-event-wizard.md)在控制項中指定您想要的事件。  
  
### 內建事件  
  
|事件|引發函式|註解|  
|--------|----------|--------|  
|按一下|**void FireClick\( \)**|當控制項捕捉到滑鼠、收到任何 **BUTTONUP** \(中間，左邊或右邊\) 訊息，或是按鈕被釋放在控制項上時引發。  內建 MouseUp 和 MouseDown 事件會在這個事件之前發生。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_CLICK\( \)**|  
|DblClick|**void FireDblClick\( \)**|類似於 Click，但當接收到 **BUTTONDBLCLK** 訊息時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_DBLCLICK\( \)**|  
|錯誤|**void FireError\( SCODE**  *scode* **, LPCSTR**  `lpszDescription` **, UINT**  `nHelpID`  **\= 0 \)**|當您的 ActiveX 控制項內發生方法呼叫或屬性存取的範圍外之錯誤時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_ERROREVENT\( \)**|  
|KeyDown|**void FireKeyDown\( short**  `nChar` **, short**  `nShiftState`  **\)**|當接收到 `WM_SYSKEYDOWN` 或 `WM_KEYDOWN` 訊息時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_KEYDOWN\( \)**|  
|KeyPress|**void FireKeyPress\( short\***  `pnChar`  **\)**|當接收到 `WM_CHAR` 訊息時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_KEYPRESS\( \)**|  
|KeyUp|**void FireKeyUp\( short**  `nChar` **, short**  `nShiftState`  **\)**|當接收到 `WM_SYSKEYUP` 或 `WM_KEYUP` 訊息時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_KEYUP\( \)**|  
|MouseDown|**void FireMouseDown\( short**  `nButton` **, short**  `nShiftState` **, float**  *x* **, float**  *y*  **\)**|如果接收到任何 **BUTTONDOWN** \(中間，左邊或右邊\) 時引發。  滑鼠會在這個事件引發之前被擷取。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_MOUSEDOWN\( \)**|  
|MouseMove|**void FireMouseMove\( short**  `nButton` **, short**  `nShiftState` **, float**  *x* **, float**  *y*  **\)**|當接收到 `WM_MOUSEMOVE` 訊息時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_MOUSEMOVE\( \)**|  
|MouseUp|**void FireMouseUp\( short**  `nButton` **, short**  `nShiftState` **, float**  *x* **, float**  *y*  **\)**|如果接收到任何 **BUTTONUP** \(中間，左邊或右邊\) 時引發。  滑鼠擷取會在這個事件引發之前釋放。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_MOUSEUP\( \)**|  
|ReadyStateChange|**void FireReadyStateChange\( \)**|當控制項因為接收到資料量而轉換至下一個就緒狀態時引發。<br /><br /> 事件對應輸入：**EVENT\_STOCK\_READYSTATECHANGE\( \)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> 使用加入事件精靈加入內建事件  
 加入內建事件會比加入自訂事件輕鬆，因為實際事件的引發是由基底類別 `COleControl` 自動處理。  下列程序將會加入內建事件至使用 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md) 所開發的控制項。  當按下按鍵且控制項正在使用中時，稱為 KeyPress 的事件引發。  這個程序也可以用來加入其他內建事件。  將選取的內建事件的名稱替換為 KeyPress。  
  
#### 若要使用加入事件精靈加入 KeyPress 內建事件  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別開啟捷徑功能表。  
  
3.  在捷徑功能表中，按一下 \[**加入**\] 後再按一下 \[**加入事件**\]。  
  
     這樣會開啟加入事件精靈。  
  
4.  在 \[**事件名稱**\] 下拉式清單中，選取 `KeyPress`。  
  
5.  按一下 \[**完成**\]。  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> 加入事件精靈為內建事件的變更  
 由於內建事件是由控制項的基底類別處理，加入事件精靈在任何情況下都不會變更您的類別宣告。  它將事件加入至控制項的事件對應，並在其 .IDL 檔案產生一個輸入。  下列程式碼行加入至控制項的事件對應，位於控制項類別實作 \(.CPP\) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 加入這些程式碼會在接受到 `WM_CHAR` 訊息以及控制項作用中時，引發 KeyPress 事件。  KeyPress 事件可以藉由呼叫其引發函式 \(例如 `FireKeyPress`\) ，在其他時間從控制代碼的內部引發。  
  
 加入事件精靈加入下列程式碼至控制項的 .IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 此行將 KeyPress 事件關聯至其標準分派 ID，並允許容器預期 KeyPress 事件。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)
---
title: "MFC ActiveX 控制項：加入自訂事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Click 事件, 自訂事件"
  - "ClickIn 事件"
  - "COleControl 類別, 自訂事件"
  - "自訂事件"
  - "自訂事件, 加入至 ActiveX 控制項"
  - "EVENT_CUSTOM 巨集"
  - "EVENT_CUSTOM 前置詞"
  - "事件 [C++], ActiveX 控制項"
  - "FireClickIn 事件"
  - "FireEvent 方法, 加入自訂事件"
  - "InCircle 方法"
  - "MFC ActiveX 控制項, 事件"
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# MFC ActiveX 控制項：加入自訂事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂事件與內建事件不同它們不是由類別 `COleControl`自動引發。  自訂事件辨識某些動作，由控制項開發人員，做為事件。  自訂事件的事件對應項目由 `EVENT_CUSTOM` 巨集表示。  下列各節實作使用 ActiveX 控制項精靈，建立的 ActiveX 控制項專案的自訂事件。  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a> 將具有的加入事件精靈的自訂事件。  
 下列程序將特定自訂事件， ClickIn。  您可以使用這個程序將其他自訂事件。  用 ClickIn 事件名稱和參數替代自訂事件名稱和其參數。  
  
#### 使用加入事件精靈，將 ClickIn 自訂事件  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別開啟捷徑功能表。  
  
3.  從捷徑功能表上，按一下 **Add** 然後按一下 \[**加入事件**\]。  
  
     這樣會開啟加入事件精靈。  
  
4.  在 **Event name** 方塊，請先選取現有事件，然後按一下 \[**自訂**\] 選項按鈕，然後輸入 `ClickIn`。  
  
5.  在 **Internal name** 方塊中，輸入事件引發函式的名稱。  對於這個範例，請使用加入事件精靈提供的預設值 \(`FireClickIn`\)。  
  
6.  將參數，呼叫 `xCoord` \(型別 `OLE_XPOS_PIXELS`\)，使用 **Parameter Name** 和 **Parameter Type** 控制。  
  
7.  將第二個參數，呼叫 `yCoord` \(型別 `OLE_YPOS_PIXELS`\)。  
  
8.  按一下以建立事件的 **Finish** 。  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a> 加入事件的自訂事件的精靈變更  
 當您將自訂事件時，將事件精靈會變更控制項的類別。H、.CPP 和 .IDL 檔案。  下列程式碼範例是專為 ClickIn 事件。  
  
 下列程式碼加入至標頭檔 \(。H\) 控制項類別檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_1.h)]  
  
 這個程式碼會宣告使用 Add 事件精靈，以 ClickIn 事件和參數的 [COleControl::FireEvent](../Topic/COleControl::FireEvent.md) 定義的內嵌函式呼叫 `FireClickIn` 。  
  
 此外，下列程式行加入至控制項的事件對應，位於控制項類別實作 \(.CPP\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 這個程式碼會將事件 ClickIn 對內嵌函式 `FireClickIn`，使用加入事件精靈，您定義的參數。  
  
 最後，下列程式行加入至控制項的 .IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 這一行會將 ClickIn 事件每個特定 ID 編號，並以加入事件精靈事件清單中的事件位置。  在事件清單中的項目可讓容器所需的事件。  例如，在中，當事件引發時，它會提供所要執行的處理常式程式碼。  
  
##  <a name="_core_calling_fireclickin"></a> 呼叫 FireClickIn  
 使用加入事件精靈，也就是您已加入 ClickIn 自訂事件，您必須決定這個事件時要引發。  您可以藉由呼叫 `FireClickIn` 時，執行這項適當動作發生時。  對於這個討論，，當使用者按一下圓形或橢圓形區域內時，控制項在 `WM_LBUTTONDOWN` 訊息處理常式內的 `InCircle` 函式 ClickIn 引發事件。  下列程序將 `WM_LBUTTONDOWN` 處理常式。  
  
#### 將事件加入精靈的訊息處理常式  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，選取您的 ActiveX 控制項類別。  
  
3.  在 \[屬性\] 視窗中，按一下 \[訊息\] 按鈕。  
  
     屬性視窗會顯示可以由 ActiveX 控制項處理的訊息清單。  會以粗體顯示的所有訊息已處理函式指派給它。  
  
4.  在屬性視窗中，選取您要處理的訊息。  對於這個範例中，選取 `WM_LBUTTONDOWN`。  
  
5.  從右邊的下拉式清單方塊中，選取 **\<Add\> OnLButtonDown**。  
  
6.  按兩下新處理常式函式類別檢視跳至 ActiveX 控制項實作 \(.CPP\) 檔案的訊息處理常式程式碼。  
  
 在滑鼠左鍵在控制項視窗中時，按一下下列程式碼範例會呼叫 **InCircle** 函式。  這個範例可以在 `WM_LBUTTONDOWN` 處理常式函式， `OnLButtonDown`中，在 [Circ 範例](../top/visual-cpp-samples.md) 。  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  將事件精靈建立滑鼠按鈕動作的目前訊息處理常式，對基底類別相同的訊息處理常式的呼叫會自動加入。  不要移除這個呼叫。  如果您的控制項使用任何內建滑鼠訊息，基底類別的訊息處理常式必須呼叫以確保滑鼠捕捉適當地管理。  
  
 在下列範例中，事件時，只有在按一下會發生在控制項中的圓形或橢圓形區域內。  若要達成這個行為，您在控制項的實作 \(.CPP\) 檔案中放置 `InCircle` 函式:  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 您也需要加入 `InCircle` 函式的宣告加入至控制項的標題 \(。H\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a> 與內建名稱的自訂事件  
 您可以建立名為的自訂事件和內建事件相同，不過，您無法實作都在相同的控制項。  例如，您可能想要建立呼叫不引發所按的自訂事件內建事件按一下時通常會引發。  您可以藉由呼叫它的函式引發隨時然後引發 Click 事件。  
  
 下列程序將自訂 Click 事件。  
  
#### 將使用內建事件名稱的自訂事件。  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別開啟捷徑功能表。  
  
3.  從捷徑功能表上，按一下 **Add** 然後按一下 \[**加入事件**\]。  
  
     這樣會開啟加入事件精靈。  
  
4.  在 **Event Name** 下拉式清單中，選取內建事件名稱。  對於這個範例，請選取 **Click**。  
  
5.  對於 **Event Type**，選取 **Custom**。  
  
6.  按一下以建立事件的 **Finish** 。  
  
7.  在適當的位置呼叫 `FireClick` 的程式碼。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)
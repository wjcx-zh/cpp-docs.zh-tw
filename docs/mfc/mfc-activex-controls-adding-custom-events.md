---
title: "MFC ActiveX 控制項： 加入自訂事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bbf62500d3aaca21e9b01401e839d08fa56755c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控制項：加入自訂事件
自訂事件與不同的內建事件的類別不會自動引發`COleControl`。 自訂的事件會辨識某些動作，由控制項開發人員，為事件。 自訂事件的事件對應項目都由`EVENT_CUSTOM`巨集。 下列章節實作 ActiveX 控制項專案使用 ActiveX 控制項精靈所建立的自訂事件。  
  
##  <a name="_core_adding_a_custom_event_with_classwizard"></a>加入與自訂事件加入事件精靈  
 下列程序會加入特定的自訂事件，ClickIn。 您可以使用此程序新增其他自訂的事件。 取代為您自訂事件的名稱和參數與 ClickIn 事件名稱及其參數。  
  
#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>若要加入使用加入事件精靈 ClickIn 自訂事件  
  
1.  載入控制項專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別若要開啟快顯功能表。  
  
3.  從捷徑功能表，按一下 **新增**，然後按一下 **加入事件**。  
  
     這會開啟 加入事件精靈。  
  
4.  在**事件名稱**方塊中，先選取現有的事件，然後按一下 **自訂**選項按鈕，然後輸入`ClickIn`。  
  
5.  在**內部名稱**方塊中，輸入此事件引發函式的名稱。 此範例中，使用加入事件精靈所提供的預設值 (`FireClickIn`)。  
  
6.  加入參數，呼叫`xCoord`(型別`OLE_XPOS_PIXELS`)，並使用**參數名稱**和**參數型別**控制項。  
  
7.  新增第二個參數，呼叫`yCoord`(型別`OLE_YPOS_PIXELS`)。  
  
8.  按一下**完成**建立的事件。  
  
##  <a name="_core_classwizard_changes_for_custom_events"></a>加入事件精靈變更的自訂事件  
 當您新增自訂的事件時，加入事件精靈會在控制項類別中進行變更。H。CPP、 和。IDL 檔案。 下列程式碼範例僅適用於 ClickIn 事件。  
  
 下列幾行加入至標頭 (。H） 檔案的控制項類別：  
  
 [!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]  
  
 此程式碼會宣告內嵌函式呼叫`FireClickIn`呼叫[COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent)參數 ClickIn 事件與您定義使用加入事件精靈。  
  
 此外，下列這一行加入至事件對應的實作中找到的控制項 (。控制項類別 CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]  
  
 此程式碼對應至內嵌函式的事件 ClickIn `FireClickIn`，傳遞您使用 加入事件精靈定義的參數。  
  
 最後，下列這一行已加入到您的控制項。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]  
  
 這一行會指派特定的 ID 編號，取自加入事件精靈的 [事件] 清單中的事件位置 ClickIn 事件。 [事件] 清單中的項目可讓容器以預測事件。 例如，它可能會提供事件引發時執行的處理常式程式碼。  
  
##  <a name="_core_calling_fireclickin"></a>呼叫 FireClickIn  
 既然您已加入使用加入事件精靈 ClickIn 自訂事件，您必須決定要引發此事件時。 您可以呼叫`FireClickIn`適當的動作就會發生。 這個討論而言，此控制項會使用`InCircle`函式內`WM_LBUTTONDOWN`引發 ClickIn 事件，當使用者按一下圓形或橢圓形的區域內部的訊息處理常式。 下列程序加入`WM_LBUTTONDOWN`處理常式。  
  
#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>加入訊息處理常式加入事件精靈  
  
1.  載入控制項專案。  
  
2.  在 類別檢視中，選取您的 ActiveX 控制項類別。  
  
3.  在 屬性 視窗中，按一下**訊息** 按鈕。  
  
     [屬性] 視窗會顯示一份可以由 ActiveX 控制項的訊息。 已經以粗體顯示任何訊息都有指派給它的處理常式函式。  
  
4.  從 [屬性] 視窗中，選取您想要處理的訊息。 此範例中，選取`WM_LBUTTONDOWN`。  
  
5.  在右側下拉式清單方塊中，從選取**\<新增 > OnLButtonDown**。  
  
6.  按兩下跳至訊息處理常式程式碼，在實作類別檢視中新的處理常式函式 (。ActiveX 控制項的 CPP) 檔案。  
  
 下列程式碼範例會呼叫**InCircle**函式每次控制視窗中按下滑鼠左的按鈕。 此範例位於`WM_LBUTTONDOWN`處理常式函式， `OnLButtonDown`，請在[Circ 範例](../visual-cpp-samples.md)抽象。  
  
 [!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]  
  
> [!NOTE]
>  當加入事件精靈建立滑鼠按鈕動作的訊息處理常式時，會自動加入至相同的訊息處理常式的基底類別呼叫。 請勿移除這個呼叫。 如果控制項可使用任何內建滑鼠訊息，必須呼叫基底類別中的訊息處理常式，以確保正確地處理滑鼠捕捉。  
  
 在下列範例中，就會引發事件只當按一下發生在控制項中的圓形或橢圓形區域內部。 若要達到這種行為，您可以放置`InCircle`函式，在您的控制項實作 (。CPP) 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]  
  
 您也必須新增下列宣告的`InCircle`函式來控制的標頭 (。H） 檔案：  
  
 [!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]  
  
##  <a name="_core_custom_events_with_stock_names"></a>自訂事件具有內建名稱  
 您可以建立自訂事件與內建的事件名稱相同，不過您可以實作在相同的控制項。 例如，您可以建立自訂事件呼叫內建事件正常引發按一下時不會引發的按一下。 您再無法藉由呼叫其引發的函式，隨時引發 Click 事件。  
  
 下列程序會加入自訂的按一下事件。  
  
#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>若要加入自訂事件使用內建事件名稱  
  
1.  載入控制項專案。  
  
2.  在類別檢視中，以滑鼠右鍵按一下您的 ActiveX 控制項類別若要開啟快顯功能表。  
  
3.  從捷徑功能表，按一下 **新增**，然後按一下 **加入事件**。  
  
     這會開啟 加入事件精靈。  
  
4.  在**事件名稱**下拉式清單中，選取 內建事件名稱。 此範例中，選取**按一下**。  
  
5.  如**事件類型**，選取**自訂**。  
  
6.  按一下**完成**建立的事件。  
  
7.  呼叫`FireClick`在程式碼中的適當位置。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)

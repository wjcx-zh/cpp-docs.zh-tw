---
title: MFC ActiveX 控制項： 加入自訂事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c4acd417dacadbe2667f63c70435b97353bafe1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384412"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控制項：加入自訂事件

自訂事件與不同的內建事件類別不會自動引發`COleControl`。 自訂事件會識別特定動作，取決於控制項開發人員，為事件。 EVENT_CUSTOM 巨集來表示自訂事件的事件對應項目。 下一節會實作 ActiveX 控制項專案使用 ActiveX 控制項精靈所建立的自訂事件。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> 新增的自訂事件加入事件精靈

下列程序會加入特定的自訂事件，ClickIn。 您可以使用此程序，以新增其他自訂的事件。 替代成您的自訂事件名稱和其 ClickIn 事件名稱和參數的參數。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>若要加入使用加入事件精靈 ClickIn 自訂事件

1. 載入控制項專案。

1. 類別檢視 中以滑鼠右鍵按一下您的 ActiveX 控制項類別，若要開啟快顯功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**新增事件**。

     這會開啟 [新增事件精靈]。

1. 在 **事件名稱**方塊中，第一次選取任何現有的事件，然後按一下**自訂**選項按鈕，然後輸入*ClickIn*。

1. 在 **內部名稱**方塊中，輸入事件引發函式的名稱。 針對此範例中，使用 加入事件精靈所提供的預設值 (`FireClickIn`)。

1. 新增名為的參數*xCoord* (型別*OLE_XPOS_PIXELS*)，並使用**參數名稱**並**參數型別**控制項。

1. 新增第二個參數，呼叫*yCoord* (型別*OLE_YPOS_PIXELS*)。

1. 按一下 **完成**建立的事件。

##  <a name="_core_classwizard_changes_for_custom_events"></a> 自訂事件加入事件精靈的變更

當您新增自訂事件時，加入事件精靈會在控制項類別中進行變更。H。CPP、 和。IDL 檔案。 下列程式碼範例專屬於 ClickIn 事件。

下列幾行加入至標頭 (。H） 檔案的控制項類別：

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此程式碼會宣告稱為內嵌函式`FireClickIn`它會呼叫[COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent)參數 ClickIn 事件與您定義使用 [新增事件精靈]。

此外下, 面這一行加入實作中找到的控制項的事件對應 (。控制項類別 CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此程式碼對應至內嵌函式的事件 ClickIn `FireClickIn`，傳遞您使用 [新增事件精靈] 定義的參數。

最後，將下列這一行加入至您的控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

這一行會將資料區間指派 ClickIn 事件特定的 ID 編號，從 [新增事件精靈] 的 [事件] 清單中的事件的位置。 [事件] 清單中的項目可讓容器，以預測事件。 比方說，它可能會提供事件引發時要執行的處理常式程式碼。

##  <a name="_core_calling_fireclickin"></a> 呼叫 FireClickIn

既然您已新增使用加入事件精靈 ClickIn 自訂事件，您必須決定要引發此事件時。 您可以呼叫`FireClickIn`適當的動作就會發生。 在本文中，控制項就會使用`InCircle`內引發 ClickIn 事件，當使用者按一下圓形或橢圓形區域內的 WM_LBUTTONDOWN 訊息處理常式函式。 下列程序新增 WM_LBUTTONDOWN 處理常式。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>若要新增的訊息處理常式加入事件精靈

1. 載入控制項專案。

1. 在類別檢視 中，選取您的 ActiveX 控制項類別。

1. 在 屬性 視窗中，按一下**訊息** 按鈕。

     [屬性] 視窗會顯示一份的 ActiveX 控制項可以處理的訊息。 已經以粗體顯示任何訊息都指派給它的處理常式函式。

1. 從 [屬性] 視窗中，選取您想要處理的訊息。 針對此範例中，選取 WM_LBUTTONDOWN。

1. 從下拉式清單方塊的右邊，選取**\<新增 > OnLButtonDown**。

1. 按兩下新的處理常式函式，在 類別檢視，可前往 訊息處理常式程式碼，在實作 (。您的 ActiveX 控制項的 CPP) 檔案。

下列程式碼範例會呼叫`InCircle`函式每次在 [控制] 視窗內按下滑鼠左的按鈕。 此範例可在 WM_LBUTTONDOWN 處理常式函式中， `OnLButtonDown`，請在[Circ 範例](../visual-cpp-samples.md)抽象。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  當 [新增事件精靈] 建立滑鼠按鈕動作的訊息處理常式時，會自動加入相同的訊息處理常式的基底類別呼叫。 請勿移除這個呼叫。 如果您的控制項可使用任何內建的滑鼠訊息，必須呼叫基底類別中的訊息處理常式，以確保正確處理滑鼠捕捉。

在下列範例中，就會引發事件只當按一下發生在控制項內的圓形或橢圓形區域內。 若要達到這種行為，您可以將放置`InCircle`函式，在您的控制項實作 (。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

您也需要加入下列宣告的`InCircle`至控制項的標頭的函式 (。H） 檔案：

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> 具有內建名稱的自訂事件

不過，您可以實作在同一個控制項，您可以建立自訂事件與內建的事件名稱相同。 例如，您可能要建立自訂事件，稱為內建事件正常引發按一下時不會引發 Click。 您接著可以在任何時間引發 Click 事件，藉由呼叫其引發函式。

下列程序將自訂的 Click 事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>若要新增自訂事件使用的內建事件名稱

1. 載入控制項專案。

1. 類別檢視 中以滑鼠右鍵按一下您的 ActiveX 控制項類別，若要開啟快顯功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**新增事件**。

     這會開啟 [新增事件精靈]。

1. 在 **事件名稱**下拉式清單中，選取 內建事件名稱。 此範例中，選取**按一下**。

1. 針對**事件型別**，選取**自訂**。

1. 按一下 **完成**建立的事件。

1. 呼叫`FireClick`程式碼中的適當位置。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

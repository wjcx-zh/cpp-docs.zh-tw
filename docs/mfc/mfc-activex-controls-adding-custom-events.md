---
title: MFC ActiveX 控制項：新增自訂事件
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
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907314"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC ActiveX 控制項：新增自訂事件

自訂事件與內建事件不同之處在于，它們不會`COleControl`由類別自動引發。 自訂事件會辨識由控制項開發人員判斷為事件的特定動作。 自訂事件的事件對應專案是由 EVENT_CUSTOM 宏表示。 下一節會針對使用 ActiveX 控制項嚮導所建立的 ActiveX 控制項專案，實作為自訂事件。

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>使用新增事件 Wizard 新增自訂事件

下列程式會新增特定的自訂事件 ClickIn。 您可以使用這個程式來新增其他自訂事件。 將您的自訂事件名稱及其參數取代為 ClickIn 事件名稱和參數。

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>若要使用新增事件 Wizard 新增 ClickIn 自訂事件

1. 載入控制項專案。

1. 在**類別檢視**中，以滑鼠右鍵按一下您的 ActiveX 控制項類別，以開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [**加入**]，然後按一下 [**新增事件**]。

   這會開啟 [新增事件嚮導]。

1. 在 [**事件名稱**] 方塊中，先選取任何現有的事件，然後按一下 [**自訂**] 選項按鈕，再輸入*ClickIn*。

1. 在 [**內部名稱**] 方塊中，輸入事件引發函式的名稱。 在此範例中，請使用 [新增事件 Wizard] （`FireClickIn`）所提供的預設值。

1. 使用**參數名稱**和**參數類型**控制項，新增名為*xCoord* （類型*OLE_XPOS_PIXELS*）的參數。

1. 新增第二個參數，稱為*yCoord* （類型*OLE_YPOS_PIXELS*）。

1. 按一下 **[完成]** 以建立事件。

##  <a name="_core_classwizard_changes_for_custom_events"></a>新增自訂事件的事件嚮導變更

當您新增自訂事件時，[新增事件嚮導] 會對控制項類別進行變更。H、。CPP 和。IDL 檔案。 下列程式碼範例是 ClickIn 事件特有的。

下列幾行會加入至標頭（。H）控制項類別的檔案：

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

此程式碼會宣告名`FireClickIn`為的內嵌函式，其會呼叫[COleControl：： FireEvent](../mfc/reference/colecontrol-class.md#fireevent)與您使用 [新增事件] Wizard 定義的 ClickIn 事件和參數。

此外，下列這一行會加入控制項的事件對應中（位於執行中（）。CPP）檔案的控制項類別：

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

此程式碼會將事件 ClickIn 對應至內嵌`FireClickIn`函式，並傳遞您使用 [新增事件] Wizard 定義的參數。

最後，會將下列這一行新增至控制項的。IDL 檔案：

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

這一行會指派一個特定的識別碼，從事件在 [新增事件] [Wizard] 事件清單中的位置所取得的 ClickIn 事件。 事件清單中的專案可讓容器預測事件。 例如，它可能會提供要在引發事件時執行的處理常式程式碼。

##  <a name="_core_calling_fireclickin"></a>呼叫 FireClickIn

現在您已使用 [新增事件] Wizard 新增 ClickIn 自訂事件，您必須決定何時要引發此事件。 您可以藉由在`FireClickIn`適當動作發生時呼叫來完成這項工作。 在此討論中，控制項會使用`InCircle` `WM_LBUTTONDOWN`訊息處理常式內的函式，在使用者于圓形或橢圓形區域內按一下時引發 ClickIn 事件。 下列`WM_LBUTTONDOWN`程式會加入處理常式。

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>使用新增事件嚮導加入訊息處理常式

1. 載入控制項專案。

1. 在 **類別檢視**中，選取您的 ActiveX 控制項類別。

1. 在 [**屬性**] 視窗中，您會看到 ActiveX 控制項可以處理的訊息清單。 以粗體顯示的任何訊息都已經有指派給它的處理函式。

1. 選取您想要處理的訊息。 針對此範例，請`WM_LBUTTONDOWN`選取。

1. 從右邊的下拉式清單方塊中，選取 **\<[新增] > OnLButtonDown**。

1. 按兩下 **類別檢視**中的新處理常式函式，跳至執行中的訊息處理常式程式碼（。CPP）檔案。

下列程式碼範例會在`InCircle`每次按一下控制項視窗內的滑鼠左鍵時呼叫函數。 此範例可在「 `WM_LBUTTONDOWN`處理`OnLButtonDown`函式」中找到，也就是在 [ [Circ 範例](../overview/visual-cpp-samples.md)] 摘要中。

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  當 [新增事件嚮導] 建立滑鼠按鍵動作的訊息處理常式時，會自動加入對基類之相同訊息處理常式的呼叫。 請勿移除此呼叫。 如果您的控制項使用任何庫存滑鼠訊息，則必須呼叫基類中的訊息處理常式，以確保正確處理滑鼠捕捉。

在下列範例中，只有當按一下動作出現在控制項內的圓形或橢圓形區域內時，才會引發事件。 若要達到這個行為，您可以將`InCircle`函式放在控制項的實作為（。CPP）檔案：

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

您也必須將下列`InCircle`函式宣告加入至控制項的標頭（。H）檔案：

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>具有庫存名稱的自訂事件

您可以使用與內建事件相同的名稱來建立自訂事件，不過，您不能在相同的控制項中同時執行這兩者。 例如，您可能會想要建立名為 Click 的自訂事件，它不會在存貨事件按正常引發時引發。 接著，您可以呼叫其引發函式，隨時引發 Click 事件。

下列程式會加入自訂的 Click 事件。

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>若要加入使用內建事件名稱的自訂事件

1. 載入控制項專案。

1. 在**類別檢視**中，以滑鼠右鍵按一下您的 ActiveX 控制項類別，以開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [**加入**]，然後按一下 [**新增事件**]。

   這會開啟 [新增事件嚮導]。

1. 在 [**事件名稱**] 下拉式清單中，選取 [內建事件名稱]。 在此範例中，選取 [**按一下**]。

1. 針對 [**事件種類**]，選取 [**自訂**]。

1. 按一下 **[完成]** 以建立事件。

1. 在`FireClick`您程式碼中的適當位置呼叫。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

---
title: MFC ActiveX 控制項：使用字型
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: 58f387ba6f4d7cdffb3ffc1f7be6f9acde8314f4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618170"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控制項：使用字型

如果您的 ActiveX 控制項顯示文字，您可以允許控制項使用者藉由變更字型屬性來變更文字外觀。 字型屬性會實作為字型物件，而且可以是下列兩種類型的其中一種： stock 或 custom。 內建字型屬性是 preimplemented 字型屬性，您可以使用 [新增屬性] Wizard 來新增。 自訂字型屬性不會 preimplemented，且控制項開發人員會決定屬性的行為和使用方式。

本文章涵蓋下列主題：

- [使用內建字型屬性](#_core_using_the_stock_font_property)

- [在控制項中使用自訂字型屬性](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>使用內建字型屬性

股票字型屬性是由類別[COleControl](reference/colecontrol-class.md)所 preimplemented。 此外，也可以使用標準字型屬性頁，讓使用者變更字型物件的各種屬性，例如其名稱、大小和樣式。

透過的[ivsfontandcolorstorage.getfont](reference/colecontrol-class.md#getfont)、 [SetFont](reference/colecontrol-class.md#setfont)和[InternalGetFont](reference/colecontrol-class.md#internalgetfont)函式來存取字型物件 `COleControl` 。 控制項使用者將透過和函式存取字型物件 `GetFont` ， `SetFont` 其方式與任何其他 Get/Set 屬性相同。 當控制項內需要字型物件的存取權時，請使用 `InternalGetFont` 函數。

如[MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)中所述，使用 [[加入屬性] Wizard](../ide/names-add-property-wizard.md)很容易加入內建屬性。 您可以選擇 [字型] 屬性，而 [加入屬性] Wizard 會自動將股票字型專案插入控制項的分派圖中。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>使用加入屬性 Wizard 加入內建字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

   這會開啟 [新增屬性] Wizard。

1. 在 [**屬性名稱**] 方塊中，按一下 [**字型**]。

1. 按一下 [完成] 。

[新增屬性] 嚮導會將下列這一行新增至控制項的分派對應，其位於控制項類別的執行檔案中：

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，[新增屬性] Wizard 會將下列這一行新增至控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

[內建標題] 屬性是 text 屬性的範例，可以使用 [內建字型] 屬性資訊來繪製。 將 [內建標題] 屬性加入至控制項時，會使用類似于 stock 字型屬性的步驟。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要使用加入屬性 Wizard 加入股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

   這會開啟 [新增屬性] Wizard。

1. 在 [**屬性名稱**] 方塊中，按一下 [**標題**]。

1. 按一下 [完成] 。

[新增屬性] 嚮導會將下列這一行新增至控制項的分派對應，其位於控制項類別的執行檔案中：

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>修改 OnDraw 函數

的預設執行會 `OnDraw` 使用 Windows 系統字型來表示控制項中顯示的所有文字。 這表示您必須在 `OnDraw` 裝置內容中選取字型物件，以修改程式碼。 若要這樣做，請呼叫[COleControl：： SelectStockFont](reference/colecontrol-class.md#selectstockfont) ，並傳遞控制項的裝置內容，如下列範例所示：

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

在函式已 `OnDraw` 修改為使用字型物件之後，控制項內的任何文字都會以控制項的股票字型屬性的特性顯示。

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>在控制項中使用自訂字型屬性

除了 [內建字型] 屬性以外，ActiveX 控制項也可以有自訂字型屬性。 若要新增自訂字型屬性，您必須：

- 使用 [加入屬性] Wizard 來執行自訂字型屬性。

- [處理字型通知](#_core_processing_font_notifications)。

- [執行新的字型通知介面](#_core_implementing_a_new_font_notification_interface)。

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>執行自訂字型屬性

若要執行自訂字型屬性，您可以使用 [加入屬性] Wizard 來加入屬性，然後對程式碼進行一些修改。 下列各節說明如何將自訂 `HeadingFont` 屬性加入至範例控制項。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>使用加入屬性 Wizard 加入自訂字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

   這會開啟 [新增屬性] Wizard。

1. 在 [**屬性名稱**] 方塊中，輸入屬性的名稱。 在此範例中，請使用**HeadingFont**。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 [**屬性類型**] 方塊中，選取 [ **IDispatch** ] 做 <strong>\*</strong> 為屬性的類型。

1. 按一下 [完成] 。

[新增屬性] Wizard 會建立程式碼，將 `HeadingFont` 自訂屬性新增至 `CSampleCtrl` 類別和範例。IDL 檔案。 因為 `HeadingFont` 是 Get/Set 屬性類型，所以 [加入屬性] Wizard 會修改 `CSampleCtrl` 類別的分派對應，以包含 DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)宏專案：

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 宏會將 `HeadingFont` 屬性名稱與其對應的 `CSampleCtrl` 類別 Get 和 Set 方法、 `GetHeadingFont` 和 `SetHeadingFont` 產生關聯。 也會指定屬性值的類型。在此情況下，請 VT_FONT。

[加入屬性] Wizard 也會在控制項標頭檔中加入宣告（。H）（適用于和函式） `GetHeadingFont` `SetHeadingFont` ，並將其函式範本加入控制項執行檔（。CPP）：

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最後，[新增屬性] Wizard 會修改控制項。IDL 檔案，方法是加入屬性的專案 `HeadingFont` ：

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>修改控制項程式碼

現在您已將屬性新增 `HeadingFont` 至控制項，您必須對控制標頭和執行檔案進行一些變更，才能完全支援新的屬性。

在控制項標頭檔中（。H），加入下列受保護成員變數的宣告：

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控制項執行檔（。CPP），請執行下列動作：

- 初始化控制項函式中的*m_fontHeading* 。

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 宣告靜態 FONTDESC 結構，其中包含字型的預設屬性。

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控制項成員函式中 `DoPropExchange` ，新增對函數的呼叫 `PX_Font` 。 這會提供自訂字型屬性的初始化和持續性。

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成控制成員函式的執行 `GetHeadingFont` 。

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成控制成員函式的執行 `SetHeadingFont` 。

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控制項成員函式 `OnDraw` 以定義變數，以保存先前選取的字型。

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控制項成員函式 `OnDraw` ，以在要使用字型的位置加入下面這一行，以選取自訂字型到裝置內容中。

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控制項成員函式 `OnDraw` ，藉由在使用字型之後加入下列這一行，以選取上一個字型回到裝置內容中。

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

在自訂字型屬性實作為之後，應該會實作為標準字型屬性頁，讓控制項使用者可以變更控制項的目前字型。 若要加入 [標準字型] 屬性頁的屬性頁識別碼，請在 BEGIN_PROPPAGEIDS 宏後面插入下列一行：

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

您也必須將 BEGIN_PROPPAGEIDS 宏的 count 參數遞增一。 下面這行程式碼可說明這點：

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

進行這些變更之後，請重建整個專案以併入額外的功能。

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>處理字型通知

在大部分情況下，控制項必須知道字型物件的特性何時已修改。 每個字型物件都能夠藉由呼叫介面的成員函式（由所實 `IFontNotification` ）來提供通知 `COleControl` 。

如果控制項使用 stock 字型屬性，其通知會由的成員函式處理 `OnFontChanged` `COleControl` 。 當您新增自訂字型屬性時，可以讓它們使用相同的執行方式。 在上一節的範例中，這是藉由在初始化*m_fontHeading*成員變數時傳遞 &*m_xFontNotification*來完成。

![實作多個字型物件介面](../mfc/media/vc373q1.gif "實作多個字型物件介面") <br/>
執行多個字型物件介面

上圖中的實線顯示這兩個字型物件都使用相同的執行 `IFontNotification` 。 如果您想要區別哪些字型已變更，這可能會造成問題。

區分控制項字型物件通知的其中一種方式，是 `IFontNotification` 針對控制項中的每個字型物件，建立個別的介面執行。 這項技術可讓您只更新使用最近修改過之字型的字串或字串，將繪圖程式碼優化。 下列各節示範針對第二個字型屬性執行個別通知介面所需的步驟。 第二個字型屬性會假設為 `HeadingFont` 上一節中所新增的屬性。

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>執行新的字型通知介面

若要區分兩個或多個字型的通知，必須針對控制項中所使用的每個字型來執行新的通知介面。 下列各節描述如何藉由修改控制項標頭和執行檔案來執行新的字型通知介面。

### <a name="additions-to-the-header-file"></a>標頭檔的新增專案

在控制項標頭檔中（。H），將下列幾行新增至類別宣告：

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

這會建立名為的 `IPropertyNotifySink` 介面執行 `HeadingFontNotify` 。 這個新介面包含名為的方法 `OnChanged` 。

### <a name="additions-to-the-implementation-file"></a>執行檔的新增專案

在初始化標題字型的程式碼（在控制項的函式中），將 &*m_xFontNotification*變更為 &*m_xHeadingFontNotify*。 然後，新增下列程式碼：

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`介面中的和方法會追蹤 `Release` `IPropertyNotifySink` ActiveX 控制項物件的參考計數。 當控制項取得介面指標的存取權時，控制項會呼叫 `AddRef` 來遞增參考計數。 當控制項以指標完成時，它會呼叫 `Release` ，其方式非常類似 `GlobalFree` 于釋放全域記憶體區塊。 當此介面的參考計數到達零時，就可以釋放介面實。 在此範例中，函式會傳回 `QueryInterface` `IPropertyNotifySink` 特定物件上介面的指標。 此函式可讓 ActiveX 控制項查詢物件，以判斷它支援的介面。

對您的專案進行這些變更之後，請重建專案，並使用測試容器來測試介面。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控制項：使用內建屬性頁](mfc-activex-controls-using-stock-property-pages.md)

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
ms.openlocfilehash: 02c52d2544afdc9d13fc3ec67ad9eed757a3f277
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499699"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控制項：使用字型

如果您的 ActiveX 控制項顯示文字，您可以藉由變更字型屬性，允許控制項使用者變更文字外觀。 字型屬性會實作為字型物件，而且可以是下列兩種類型之一： stock 或 custom。 [內建字型] 屬性是 preimplemented 的字型屬性，您可以使用 [加入屬性] Wizard 來加入這些屬性。 自訂字型屬性不會 preimplemented，而且控制項開發人員會判斷屬性的行為和使用方式。

本文章涵蓋下列主題：

- [使用股票字型屬性](#_core_using_the_stock_font_property)

- [在控制項中使用自訂字型屬性](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a> 使用股票字型屬性

類別 [COleControl](reference/colecontrol-class.md)會 Preimplemented 股票字型屬性。 此外，也可以使用標準字型屬性頁，讓使用者變更字型物件的各種屬性，例如其名稱、大小和樣式。

透過的 [GetFont](reference/colecontrol-class.md#getfont)、 [SetFont](reference/colecontrol-class.md#setfont)和 [InternalGetFont](reference/colecontrol-class.md#internalgetfont) 函數存取字型物件 `COleControl` 。 控制項使用者將透過和函式存取字型物件 `GetFont` ， `SetFont` 其方式與任何其他 Get/Set 屬性相同。 當控制項內需要存取字型物件時，請使用 `InternalGetFont` 函數。

如 [MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)中所述，使用 [ [加入屬性] Wizard](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)可輕鬆地加入內建屬性。 您可以選擇 [字型] 屬性，[加入屬性] 嚮導會自動將股票字型專案插入控制項的分派對應中。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>若要使用 [加入屬性] Wizard 來新增股票字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入屬性**]。

   這會開啟 [加入屬性] Wizard。

1. 在 [ **屬性名稱** ] 方塊中，按一下 [ **字型**]。

1. 按一下 [完成] 。

[新增屬性] Wizard 會將下列這一行新增至控制項的分派對應，位於控制項類別的 [執行] 檔案中：

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，[加入屬性] Wizard 也會將下列這一行加入控制項中。IDL 檔案：

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Stock Caption 屬性是可使用內建字型屬性資訊繪製的 text 屬性範例。 將 [股票標題] 屬性加入至控制項時，會使用與 [股票字型] 屬性所使用的類似步驟。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用新增屬性 Wizard 來新增股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入屬性**]。

   這會開啟 [加入屬性] Wizard。

1. 在 [ **屬性名稱** ] 方塊中，按一下 [ **標題**]。

1. 按一下 [完成] 。

[新增屬性] Wizard 會將下列這一行新增至控制項的分派對應，位於控制項類別的 [執行] 檔案中：

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函數

的預設執行會 `OnDraw` 針對控制項中顯示的所有文字使用 Windows 系統字型。 這表示您必須在 `OnDraw` 裝置內容中選取字型物件來修改程式碼。 若要這樣做，請呼叫 [COleControl：： SelectStockFont](reference/colecontrol-class.md#selectstockfont) 並傳遞控制項的裝置內容，如下列範例所示：

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

修改函式 `OnDraw` 以使用字型物件之後，就會顯示控制項內的任何文字，以及控制項的內建字型屬性的特性。

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a> 在控制項中使用自訂字型屬性

除了股票字型屬性之外，ActiveX 控制項也可以有自訂字型屬性。 若要加入自訂字型屬性，您必須：

- 您可以使用 [加入屬性] 嚮導來執行自訂字型屬性。

- [處理字型通知](#_core_processing_font_notifications)。

- [執行新的字型通知介面](#_core_implementing_a_new_font_notification_interface)。

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a> 執行自訂字型屬性

若要執行自訂字型屬性，請使用 [加入屬性] Wizard 加入屬性，然後對程式碼進行一些修改。 下列各節說明如何將自訂 `HeadingFont` 屬性加入至範例控制項。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>使用加入屬性 Wizard 加入自訂字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入屬性**]。

   這會開啟 [加入屬性] Wizard。

1. 在 [ **屬性名稱** ] 方塊中，輸入屬性的名稱。 在此範例中，請使用 **HeadingFont**。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 [**屬性類型**] 方塊中，選取 [ **IDispatch** ] 做 <strong>\*</strong> 為屬性的類型。

1. 按一下 [完成] 。

[新增屬性] Wizard 會建立程式碼，以將 `HeadingFont` 自訂屬性加入至 `CSampleCtrl` 類別和範例。IDL 檔案。 因為 `HeadingFont` 是 Get/Set 屬性型別，所以 Add 屬性 Wizard 會修改 `CSampleCtrl` 類別的分派對應，以包含 DISP_PROPERTY_EX_ID 的[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex) 宏專案：

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 宏會將 `HeadingFont` 屬性名稱與其對應的 `CSampleCtrl` 類別 Get 和 Set 方法建立關聯， `GetHeadingFont` 以及 `SetHeadingFont` 。 也會指定屬性值的類型;在此情況下，VT_FONT。

[加入屬性] Wizard 也會將 ( 中的宣告加入至控制項標頭檔中。H) 和函 `GetHeadingFont` 式 `SetHeadingFont` ，並將其函式樣板加入至控制項執行檔 (。CPP) ：

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最後，[加入屬性] Wizard 會修改控制項。IDL 檔案，方法是新增屬性的專案 `HeadingFont` ：

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>控制項程式碼的修改

現在您已將屬性加入 `HeadingFont` 至控制項，您必須對控制標頭和執行檔進行一些變更，才能完全支援新的屬性。

在控制項標頭檔中 (。H) ，請新增下列受保護成員變數的宣告：

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控制項執行檔 (。) 的 CPP，請執行下列動作：

- 在控制項的函式中初始化 *m_fontHeading* 。

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 宣告靜態 FONTDESC 結構，其中包含字型的預設屬性。

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控制項成員函式中 `DoPropExchange` ，加入對函數的呼叫 `PX_Font` 。 這會提供自訂字型屬性的初始化和持續性。

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成控制成員函式的執行 `GetHeadingFont` 。

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成控制成員函式的執行 `SetHeadingFont` 。

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控制項成員函式 `OnDraw` ，以定義變數來保存先前選取的字型。

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控制項成員函式 `OnDraw` ，藉由在使用字型的任何位置新增下列程式程式碼，以選取自訂字型至裝置內容。

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控制項成員函式 `OnDraw` ，藉由在使用字型之後加入下行，將上一個字型選取回裝置內容。

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

在執行自訂字型屬性之後，應執行標準字型屬性頁，讓控制項使用者變更控制項的目前字型。 若要加入 [標準字型] 屬性頁的屬性頁識別碼，請在 BEGIN_PROPPAGEIDS 宏之後插入下列這一行：

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

您也必須將 BEGIN_PROPPAGEIDS 宏的 count 參數遞增一。 下面這行程式碼可說明這點：

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

進行這些變更之後，請重建整個專案以納入額外的功能。

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a> 處理字型通知

在大部分的情況下，控制項必須知道字型物件的特性何時已修改。 每個字型物件都可以藉由呼叫介面的成員函式 `IFontNotification` （由所執行）來提供通知 `COleControl` 。

如果控制項使用 [內建字型] 屬性，則其通知是由的成員函式處理 `OnFontChanged` `COleControl` 。 當您加入自訂字型屬性時，您可以讓它們使用相同的實作為。 在上一節的範例中，這是藉由在初始化*m_fontHeading*成員變數時傳遞 &*m_xFontNotification*來完成。

![實作多個字型物件介面](../mfc/media/vc373q1.gif "實作多個字型物件介面") <br/>
執行多個字型物件介面

上圖中的實線顯示這兩個字型物件都使用相同的實作為 `IFontNotification` 。 如果您想要區分哪些字型有所變更，這可能會造成問題。

區分控制項字型物件通知的其中一種方式，是為 `IFontNotification` 控制項中的每個字型物件建立個別的介面實作為。 這項技術可讓您只更新使用最近修改過字型的字串或字串，以優化您的繪圖程式碼。 下列各節將示範為第二個字型屬性執行個別通知介面所需的步驟。 第二個字型屬性會假設為在 `HeadingFont` 上一節中新增的屬性。

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a> 執行新的字型通知介面

若要區分兩個或多個字型的通知，必須針對控制項中使用的每個字型來執行新的通知介面。 下列各節描述如何藉由修改控制標頭和實檔案來執行新的字型通知介面。

### <a name="additions-to-the-header-file"></a>標頭檔中的新增專案

在控制項標頭檔中 (。H) ，將下列幾行加入至類別宣告：

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

這會建立名為的 `IPropertyNotifySink` 介面實作為 `HeadingFontNotify` 。 這個新的介面包含名為的方法 `OnChanged` 。

### <a name="additions-to-the-implementation-file"></a>在執行檔中新增

在 (控制項) 中的標題字型初始化的程式碼中，將 &*m_xFontNotification* 變更為 &*m_xHeadingFontNotify*。 然後，新增下列程式碼：

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`介面中的和方法會追蹤 `Release` `IPropertyNotifySink` ActiveX 控制項物件的參考計數。 當控制項取得介面指標的存取權時，控制項會呼叫 `AddRef` 來遞增參考計數。 當控制項完成指標時，它會呼叫，就像呼叫 `Release` `GlobalFree` 來釋放全域記憶體區塊一樣。 當這個介面的參考計數移至零時，就可以釋放介面實值。 在此範例中，函式會將 `QueryInterface` 指標傳回至 `IPropertyNotifySink` 特定物件上的介面。 此函式可讓 ActiveX 控制項查詢物件，以判斷它支援的介面。

對專案進行這些變更之後，請重建專案並使用測試容器來測試介面。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控制項：使用內建屬性頁](mfc-activex-controls-using-stock-property-pages.md)

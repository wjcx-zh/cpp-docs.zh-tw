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
ms.openlocfilehash: ce1e913bb3bd1c3b74db43dc02d9d360b9cfd00c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271303"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控制項：使用字型

如果您的 ActiveX 控制項顯示文字，您可以允許控制項使用者藉由變更 font 屬性變更的文字外觀。 字型屬性會實作為字型物件，而且可以是下列其中一種： 內建或自訂。 內建字型屬性是您可以使用 [新增屬性精靈] 新增的預先實作的字型屬性。 自訂的字型屬性是不預先實作並控制項開發人員判斷屬性的行為和使用方式。

本文章涵蓋下列主題：

- [使用內建字型屬性](#_core_using_the_stock_font_property)

- [在您的控制項中使用自訂的字型屬性](#_core_implementing_a_custom_font_property)

##  <a name="_core_using_the_stock_font_property"></a> 使用內建字型屬性

內建字型屬性會預先實作由類別[COleControl](../mfc/reference/colecontrol-class.md)。 此外，標準的字型屬性頁也會提供，可讓使用者變更各種字型物件，例如其名稱、 大小和樣式屬性。

存取字型物件，可透過[GetFont](../mfc/reference/colecontrol-class.md#getfont)， [SetFont](../mfc/reference/colecontrol-class.md#setfont)，並[InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函式的`COleControl`。 控制使用者會存取字型物件，透過`GetFont`和`SetFont`函式中任何其他的 Get/Set 屬性相同的方式。 從控制項內需要字型物件的存取權時，使用`InternalGetFont`函式。

中所述[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)，將新增內建屬性是讓您輕鬆[加入屬性精靈](../ide/names-add-property-wizard.md)。 選擇 字型 屬性中，並加入屬性精靈 會自動插入控制項的分派對應內建字型項目。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>若要加入使用 [新增屬性精靈] 的內建字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

   這會開啟 [新增屬性精靈]。

1. 在 **屬性名稱**方塊中，按一下**字型**。

1. 按一下 [ **完成**]。

加入屬性精靈 會將控制項的分派對應，位於控制項類別實作檔中的下面這一行：

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，加入屬性精靈 會將下面這一行加入至控制項。IDL 檔案：

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

內建的 [標題] 屬性是可以使用內建的字型屬性資訊來繪製的文字屬性的範例。 加入至控制項的內建 Caption 屬性會使用步驟類似於所使用的內建字型屬性。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要新增內建的 Caption 屬性使用 加入屬性精靈

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

   這會開啟 [新增屬性精靈]。

1. 在 **屬性名稱**方塊中，按一下**標題**。

1. 按一下 [ **完成**]。

加入屬性精靈 會將控制項的分派對應，位於控制項類別實作檔中的下面這一行：

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

##  <a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函式

預設實作`OnDraw`使用 Windows 系統字型的所有控制項中顯示的文字。 這表示您必須修改`OnDraw`選取字型物件放入裝置內容的程式碼。 若要這樣做，請呼叫[COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont)並傳遞控制的裝置內容，如下列範例所示：

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

之後`OnDraw`函式已修改成使用字型物件，在控制項內的任何文字會顯示從控制項的內建字型屬性的特性。

##  <a name="_core_using_custom_font_properties_in_your_control"></a> 在您的控制項中使用自訂的字型屬性

除了內建的字型屬性，ActiveX 控制項有自訂的字型屬性。 若要新增自訂的字型屬性，您必須：

- 使用 [新增屬性精靈] 來實作自訂的字型屬性。

- [處理字型通知](#_core_processing_font_notifications)。

- [實作新的字型通知介面](#_core_implementing_a_new_font_notification_interface)。

###  <a name="_core_implementing_a_custom_font_property"></a> 實作自訂的字型屬性

若要實作自訂的字型屬性中,，您可以使用加入屬性精靈 來新增屬性，然後再進行一些修改的程式碼。 下列各節說明如何新增自訂`HeadingFont`範例控制項的屬性。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>若要加入自訂的字型屬性使用加入屬性精靈

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

   這會開啟 [新增屬性精靈]。

1. 在 **屬性名稱**方塊中，輸入屬性的名稱。 此範例中，使用**HeadingFont**。

1. 在 [實作類型] 中，按一下 [Get/Set 方法] 。

1. 在 **屬性型別**方塊中，選取**IDispatch** <strong>\*</strong>屬性的類型。

1. 按一下 [ **完成**]。

加入屬性精靈 建立程式碼來新增`HeadingFont`自訂屬性來`CSampleCtrl`類別和範例。IDL 檔案。 因為`HeadingFont`是 Get/Set 屬性類型，加入屬性精靈修改`CSampleCtrl`類別的分派對應，以包含 DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)巨集項目：

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 巨集產生關聯`HeadingFont`與其對應的屬性名稱`CSampleCtrl`類別 Get 和 Set 方法`GetHeadingFont`和`SetHeadingFont`。 同時指定屬性值的型別;在此情況下，VT_FONT。

加入屬性精靈也會宣告在控制項標頭檔 (。H） 針對`GetHeadingFont`和`SetHeadingFont`函式，並在控制項實作檔中將其函式樣板 (。CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最後，加入屬性精靈修改控制項。IDL 檔案中新增的項目`HeadingFont`屬性：

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>修改控制項的程式碼

既然您已新增`HeadingFont`至控制項的屬性，您必須進行一些變更以控制標頭和實作檔案，以完整支援新的屬性。

在控制項標頭檔 (。H） 中，新增下列受保護的成員變數的宣告：

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控制項實作檔 (。CPP)，執行下列動作：

- 初始化*m_fontHeading*控制建構函式中。

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 宣告靜態的 FONTDESC 結構，包含字型的預設屬性。

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 控制項中`DoPropExchange`成員函式中，將呼叫加入`PX_Font`函式。 這會提供初始設定和持續性自訂的字型屬性。

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成實作控制項`GetHeadingFont`成員函式。

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成實作控制項`SetHeadingFont`成員函式。

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控制項`OnDraw`成員函式來定義一個變數來保存先前選取的字型。

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控制項`OnDraw`放入裝置內容選取自訂的字型，藉由新增下面這行每當字型時要使用的成員函式。

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控制項`OnDraw`成員函式，來選取回裝置內容的上一個字型字型用完之後，加入下列這一行。

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

在實作自訂的字型屬性之後，應該被實作標準的 [字型] 屬性頁面允許控制項使用者變更控制項的目前字型。 若要加入屬性頁 ID，標準的字型屬性頁，請 BEGIN_PROPPAGEIDS 巨集之後插入下面這一行：

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

您也必須逐一遞增 BEGIN_PROPPAGEIDS 巨集的計數參數。 下面這行程式碼可說明這點：

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

在進行這些變更之後，重建整個專案以加入其他功能。

###  <a name="_core_processing_font_notifications"></a> 處理字型通知

在大部分情況下控制項需要知道何時已修改字型物件的特性。 每個字型物件可以藉由呼叫成員函式的變更時提供通知`IFontNotification`所實作的介面`COleControl`。

如果控制項使用內建字型屬性，其通知則由`OnFontChanged`成員函式`COleControl`。 當您新增自訂的字型屬性時，您可以讓它們使用相同的實作。 在上一節範例中，這透過傳遞 &*m_xFontNotification*初始化時*m_fontHeading*成員變數。

![實作多個字型物件介面](../mfc/media/vc373q1.gif "實作多個字型物件介面") <br/>
實作多個字型物件介面

在上圖中的實心線條顯示這兩個字型物件所使用的相同實作`IFontNotification`。 如果您想要區別哪些字型變更，這可能會造成問題。

若要建立的個別實作方法之一來區分控制項的字型物件通知是`IFontNotification`控制項中每個字型物件介面。 這項技術可讓您最佳化您的繪圖程式碼，藉由更新僅字串或字串，使用最近已修改的字型。 下列各節示範如何實作第二個的字型屬性的個別通知介面所需的步驟。 第二個字型屬性會假設為`HeadingFont`上一節中所新增的屬性。

###  <a name="_core_implementing_a_new_font_notification_interface"></a> 實作新的字型通知介面

若要區別兩個或多個字型的通知，新的通知介面必須實作的每個控制項中所使用的字型。 下列各節說明如何藉由修改控制項標頭和實作檔案中實作新的字型告知介面。

### <a name="additions-to-the-header-file"></a>新增標頭檔的項目

在控制項標頭檔 (。H），在類別宣告中加入下列幾行：

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

這會建立實作`IPropertyNotifySink`介面呼叫`HeadingFontNotify`。 這個新的介面包含呼叫的方法`OnChanged`。

### <a name="additions-to-the-implementation-file"></a>實作檔案新增項目

在初始化 （以控制建構函式） 的標題字型的程式碼，變更 &*m_xFontNotification*要 &*m_xHeadingFontNotify*。 然後新增下列程式碼：

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`並`Release`中的方法`IPropertyNotifySink`追蹤的介面的 ActiveX 控制項物件的參考計數。 當控制項取得存取權的介面指標時，控制項便會呼叫`AddRef`来遞增參考計數。 當控制項完成的指標時，它會呼叫`Release`，在大致相同方式來`GlobalFree`可能呼叫以釋放全域記憶體區塊。 此介面的參考計數歸零時，就可以釋放介面實作。 在此範例中，`QueryInterface`函式會傳回的指標`IPropertyNotifySink`特定物件上的介面。 此函式可讓查詢的物件，以判斷哪個介面支援 ActiveX 控制項。

這些變更已對您的專案之後，重建專案，並使用測試容器測試該介面。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

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
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358264"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控制項：使用字型

如果 ActiveX 控制件顯示文本,則可以允許控制項使用者透過更改字體屬性來更改文本外觀。 字體屬性作為字體對象實現,可以是兩種類型之一:股票或自定義。 "庫存字型"屬性是預先實現的字體屬性,您可以使用"添加屬性嚮導"添加這些屬性。 自定義字體屬性未預先實現,控制件開發人員確定屬性的行為和使用方式。

本文章涵蓋下列主題：

- [使用「庫存字型」 屬性](#_core_using_the_stock_font_property)

- [用自訂字型屬性](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>使用股票字型屬性

股票字體屬性由類[COleControl](../mfc/reference/colecontrol-class.md)預先實現。 此外,還提供標準 Font 屬性頁,允許使用者更改字體物件的各種屬性,如其名稱、大小和樣式。

通過[GetFont、SetFont](../mfc/reference/colecontrol-class.md#getfont)和[SetFont](../mfc/reference/colecontrol-class.md#setfont)[的內部 GetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函`COleControl`數訪問字體 物件。 控制項使用者將透過`GetFont`和`SetFont`函數以與任何其他 Get/Set 屬性相同的方式存取字型物件。 當需要從控制項中存取字型物件時,請`InternalGetFont`使用函數。

如[MFC ActiveX 控制件:屬性中](../mfc/mfc-activex-controls-properties.md)所述,[添加屬性精靈](../ide/names-add-property-wizard.md)很容易添加股票屬性。 選擇"字型"屬性,添加屬性嚮導會自動將"股票字體"條目插入到控制項的調度映射中。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>使用「新增屬性精靈」新增股票字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這將打開「添加屬性嚮導」。

1. 在 **「屬性名稱」** 框中,按下 **「字型**」 。。

1. 按一下 [完成] 。

新增屬性精靈將以下行新增到位於控制項類別實用檔案中的控制項調度對應中:

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外,「新增屬性精靈」將以下行添加到控制項 。IDL 檔案:

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

股票標題屬性是可以使用股票字體屬性資訊繪製的文本屬性的範例。 將股票標題屬性添加到控制項使用的步驟類似於用於股票字體屬性的步驟。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用新增屬性精靈加入股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這將打開「添加屬性嚮導」。

1. 在 **「屬性名稱」** 框中,按下 **「標題**」。

1. 按一下 [完成] 。

新增屬性精靈將以下行新增到位於控制項類別實用檔案中的控制項調度對應中:

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>修改 OnDraw 函數

的`OnDraw`預設實現對控制項中顯示的所有文本使用 Windows 系統字型。 這意味著您必須通過在設備上下文中選擇字體`OnDraw`物件來修改代碼。 為此,請致電[COleControl:選擇StockFont](../mfc/reference/colecontrol-class.md#selectstockfont)並傳遞控制項的裝置上下文,如以下範例所示:

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

修改該`OnDraw`函數以使用字體物件後,控制項中的任何文本都顯示具有控制項的「字體」屬性的特徵。

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>用自訂字型屬性

除了股票字體屬性外,ActiveX 控件還可以具有自定義字體屬性。 要新增自訂字型屬性,您必須:

- 使用「添加屬性嚮導」實現自訂字體屬性。

- [處理字型通知](#_core_processing_font_notifications)。

- [完整新的字型通知介面](#_core_implementing_a_new_font_notification_interface)。

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>實現自訂字型屬性

要實現自定義 Font 屬性,請使用「添加屬性嚮導」添加該屬性,然後對代碼進行一些修改。 以下各節介紹如何將自定義`HeadingFont`屬性添加到範例控制項。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>使用「新增屬性精靈」新增自訂字型屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這將打開「添加屬性嚮導」。

1. 在 **「屬性名稱」** 框中,鍵入屬性的名稱。 這個選項, 請使用**標題字型**。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 在 **「屬性類型」** 框中,為屬性的類型選擇**IDispatch。** <strong>\*</strong>

1. 按一下 [完成] 。

"新增屬性精靈"創建代碼以將`HeadingFont`自定義屬性添加到`CSampleCtrl`類和 SAMPLE。IDL 檔。 由於`HeadingFont`是 Get/Set 屬性類型,因此「新增屬性`CSampleCtrl`精靈」 修改類別的調度映射以包含[DISP_PROPERTY_EX_IDDISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)宏條目:

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX`HeadingFont`巨集設定名稱`CSampleCtrl`與其相應的類別的取得與設定方法關聯,`GetHeadingFont``SetHeadingFont`以及 。 屬性值的類型也指定;因此,屬性值的類型也指定為屬性值。在這種情況下,VT_FONT。

添加屬性精靈還會在控制項標頭檔 (中添加聲明。H)`GetHeadingFont``SetHeadingFont`的和 函數,並在控制項實現檔 (中添加其函數範本 (。CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最後,「添加屬性嚮導」修改控件。以新增`HeadingFont`屬性的項目來提交 IDL 檔:

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>控制程式碼的變更

現在,您已將`HeadingFont`該屬性添加到控制項中,您必須對控制項標頭和實現檔進行一些更改,以完全支援新屬性。

在控制項檔 (.H),添加受保護成員變數的以下聲明:

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控制項實現檔案中 (.CPP),執行以下操作:

- 初始化控制項構造函數中的*m_fontHeading。*

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 聲明包含字體預設屬性的靜態 FONTDESC 結構。

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控件`DoPropExchange`成員函數中,向函`PX_Font`數 添加調用。 這為自訂「字體」屬性提供了初始化和持久性。

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成實現控制`GetHeadingFont`成員函數。

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成實現控制`SetHeadingFont`成員函數。

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控制項`OnDraw`成員函數以定義變數以儲存以前選定的字體。

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控制項`OnDraw`成員函數,透過在使用字型的任意位置添加下一行,將自訂字型添加到設備上下文中。

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控件`OnDraw`成員函數,在使用字體後添加下一行,將以前的字體重新選擇回設備上下文。

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

實現自定義 Font 屬性後,應實現標準字體屬性頁,允許控制件使用者更改控制項的當前字型。 要新增標準 Font 屬性頁的屬性頁 ID,請在BEGIN_PROPPAGEIDS宏後插入以下行:

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

您還必須將BEGIN_PROPPAGEIDS宏的計數參數增加一個。 下面這行程式碼可說明這點：

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

進行這些更改後,重建整個專案以合併其他功能。

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>處理字型通知

在大多數情況下,控件需要知道字體對象的特徵何時被修改。 每個字體物件都能夠通過在更改時通過調用由 實現`IFontNotification``COleControl`的介面的成員函數來提供通知。

如果控件使用股票字體屬性,則其通知由`OnFontChanged`的成員`COleControl`函數處理。 添加自定義字體屬性時,可以讓它們使用相同的實現。 在上一節中的示例中,通過在初始化*m_fontHeading*成員變數時傳遞 *&m_xFontNotification*來實現這一點。

![實作多個字型物件介面](../mfc/media/vc373q1.gif "實作多個字型物件介面") <br/>
實現多個字型物件介面

上圖中的實體顯示兩個字型物件都使用相同的實作`IFontNotification`。 如果要區分更改的字體,可能會導致問題。

區分控制項的字型物件通知的一種方法是為控制項中的每個字體對象`IFontNotification`創建介面的單獨實現。 此技術允許您僅更新使用最近修改的字型的字串或字串來優化繪圖代碼。 以下各節演示了為第二個 Font 屬性實現單獨的通知介面所需的步驟。 第二個字體屬性假定為上一`HeadingFont`節中添加的屬性。

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>實現新的字型通知介面

要區分兩種或兩種以上字體的通知,必須為控制項中使用的每個字體實現一個新的通知介面。 以下各節介紹如何通過修改控制項標頭和實現文件來實現新的字體通知介面。

### <a name="additions-to-the-header-file"></a>標題檔案新增

在控制項檔 (.H),向類聲明添加以下行:

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

這將創建稱為`IPropertyNotifySink``HeadingFontNotify`的介面的實現。 此新介面包含一個稱為`OnChanged`的方法。

### <a name="additions-to-the-implementation-file"></a>新增檔案新增

在初始化標題字型的代碼(在控制項建構函數中),將 *&m_xFontNotification*變更為 *&m_xHeadingFontNotify*。 然後，新增下列程式碼：

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

介面`AddRef`中的`Release``IPropertyNotifySink`和方法跟蹤 ActiveX 控制件物件的引用計數。 當控件獲得對介面指標的訪問時,控件調用`AddRef`以增加引用計數。 當控件使用指標完成時,它將調用`Release`,其方式與調用以釋放全域`GlobalFree`記憶體的方式大致相同。 當此介面的引用計數為零時,可以釋放介面實現。 在此範例中,`QueryInterface`函數傳回指向特定`IPropertyNotifySink`物件上的 介面的指標。 此函數允許 ActiveX 控制件查詢物件以確定它支援哪些介面。

對專案進行這些更改後,重新生成專案並使用測試容器測試介面。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

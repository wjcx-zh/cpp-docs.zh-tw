---
title: "MFC ActiveX 控制項： 使用字型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a788285aed8e8b7483e13c954ee193aca69d1100
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控制項：使用字型
如果您的 ActiveX 控制項中顯示文字，您可以允許控制項使用者藉由變更 font 屬性變更的文字外觀。 會實作為字型物件字型屬性，而且可以是下列其中一種： 內建或自訂。 內建字型屬性是預先實作的字型屬性，您可以使用 [加入屬性精靈] 來新增。 自訂的字型屬性都未預先實作，讓控制項開發人員決定屬性的行為和使用方式。  
  
 本文涵蓋下列主題：  
  
-   [使用內建字型屬性](#_core_using_the_stock_font_property)  
  
-   [在控制項中使用自訂的字型屬性](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a>使用內建字型屬性  
 內建字型屬性會預先實作類別所[COleControl](../mfc/reference/colecontrol-class.md)。 此外，標準的字型屬性頁也是可用，允許使用者變更字型物件，例如其名稱、 大小和樣式的各種屬性。  
  
 存取字型物件透過[GetFont](../mfc/reference/colecontrol-class.md#getfont)， [SetFont](../mfc/reference/colecontrol-class.md#setfont)，和[InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函式的`COleControl`。 控制使用者的存取字型物件，透過`GetFont`和`SetFont`函式中任何其他的 Get/Set 屬性相同的方式。 在控制項中需要從字型物件的存取權時，請使用`InternalGetFont`函式。  
  
 中所述[MFC ActiveX 控制項： 屬性](../mfc/mfc-activex-controls-properties.md)，加入內建屬性很容易與[加入屬性精靈](../ide/names-add-property-wizard.md)。 您選擇的字型屬性，並加入屬性精靈 會自動插入至控制項的分派對應的內建字型項目。  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>若要加入使用 [加入屬性精靈] 的內建字型屬性  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟 [加入屬性精靈]。  
  
5.  在**屬性名稱**方塊中，按一下**字型**。  
  
6.  按一下 [ **完成**]。  
  
 加入屬性精靈 會將下列這一行，加入控制項的分派對應，位於控制項類別實作檔中：  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 此外，[加入屬性精靈] 會將下行加入控制項。IDL 檔案：  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 內建的標題屬性是可以使用內建字型屬性資訊來繪製的文字屬性的範例。 將內建標題屬性加入至控制項時，會使用步驟類似於所使用的內建字型屬性。  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要加入內建的標題屬性使用 加入屬性精靈  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟 [加入屬性精靈]。  
  
5.  在**屬性名稱**方塊中，按一下**標題**。  
  
6.  按一下 [ **完成**]。  
  
 加入屬性精靈 會將下列這一行，加入控制項的分派對應，位於控制項類別實作檔中：  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a>修改 OnDraw 函式  
 預設實作`OnDraw`使用 Windows 系統字型的所有文字控制項中顯示。 這表示您必須修改`OnDraw`選取字型物件放入裝置內容的程式碼。 若要這樣做，請呼叫[COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont)並傳遞控制項的裝置內容，如下列範例所示：  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 之後`OnDraw`函式已修改成使用字型物件時，控制項內的任何文字會顯示從控制項的內建字型屬性的特性。  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a>在控制項中使用自訂的字型屬性  
 除了內建字型屬性，ActiveX 控制項有自訂的字型屬性。 若要新增自訂的字型屬性，您必須：  
  
-   使用 [加入屬性精靈] 來實作自訂的字型屬性。  
  
-   [處理字型通知](#_core_processing_font_notifications)。  
  
-   [實作新字型通知介面](#_core_implementing_a_new_font_notification_interface)。  
  
###  <a name="_core_implementing_a_custom_font_property"></a>實作自訂的字型屬性  
 若要實作自訂的字型屬性，您可以使用 [加入屬性精靈] 來加入屬性，再進行一些修改，以程式碼。 下列章節說明如何將自訂`HeadingFont`範例控制項的屬性。  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>若要加入自訂的字型屬性使用 加入屬性精靈  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟 [加入屬性精靈]。  
  
5.  在**屬性名稱**方塊中，輸入屬性的名稱。 此範例中，使用**HeadingFont**。  
  
6.  在 [實作類型] 中，按一下 [Get/Set 方法] 。  
  
7.  在**屬性型別**方塊中，選取**IDispatch\*** 屬性的類型。  
  
8.  按一下 [ **完成**]。  
  
 加入屬性精靈 建立程式碼以加入`HeadingFont`自訂屬性來`CSampleCtrl`類別和範例。IDL 檔案。 因為`HeadingFont`是 Get/Set 屬性類型，加入屬性精靈 修改`CSampleCtrl`類別的分派對應，以包含`DISP_PROPERTY_EX_ID` [DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)巨集項目：  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 `DISP_PROPERTY_EX`巨集產生關聯`HeadingFont`與其對應的屬性名稱`CSampleCtrl`類別 Get 和 Set 方法，`GetHeadingFont`和`SetHeadingFont`。 同時指定屬性值的型別。在此情況下， **VT_FONT**。  
  
 加入屬性精靈 也會在控制項標頭檔 (。H） 如`GetHeadingFont`和`SetHeadingFont`函式，並在控制項實作檔中加入其函式樣板 (。CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 最後，加入屬性精靈 修改控制項。IDL 檔案新增的項目`HeadingFont`屬性：  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>修改控制項的程式碼  
 既然您已加入`HeadingFont`屬性來控制，您必須進行一些變更以控制標頭和實作檔案的完整支援新的屬性。  
  
 在控制項標頭檔 (。H） 中，加入下列的受保護的成員變數宣告：  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 在控制項實作檔 (。CPP)，執行下列動作：  
  
-   初始化`m_fontHeading`控制建構函式中。  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   宣告靜態**FONTDESC**結構，包含字型的預設屬性。  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   在控制項中`DoPropExchange`成員函式中，將呼叫加入`PX_Font`函式。 這會提供初始設定和自訂的字型屬性持續性。  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   完成實作控制`GetHeadingFont`成員函式。  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   完成實作控制`SetHeadingFont`成員函式。  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   修改控制項`OnDraw`成員函式來定義變數，以保留的先前選取的字型。  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   修改控制項`OnDraw`成員函式來加入下列程式行會只要字型是用來將自訂字型選取放入裝置內容。  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   修改控制項`OnDraw`成員函式來選取先前字型回裝置內容，將下列這一行加入之後已使用的字型。  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 實作自訂的字型屬性之後，標準的字型屬性頁應該實作，允許控制項使用者變更控制項的目前字型。 若要加入屬性頁 ID，標準的字型屬性頁，插入後的下行`BEGIN_PROPPAGEIDS`巨集：  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 您也必須將 `BEGIN_PROPPAGEIDS` 巨集的計數參數設成以 1 遞增。 下面這行程式碼可說明這點：  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 在進行這些變更之後，重建整個專案以加入其他功能。  
  
###  <a name="_core_processing_font_notifications"></a>處理字型通知  
 在大部分情況下控制項需要知道何時已修改字型物件特性。 每個字型物件是能夠提供通知，當您藉由呼叫成員函式的監視變更**IFontNotification**所實作的介面`COleControl`。  
  
 如果控制項使用內建字型屬性，其通知由處理`OnFontChanged`成員函式`COleControl`。 當您新增自訂的字型屬性時，您可以讓它們使用相同的實作。 在上一節中範例中，這藉由傳遞完成 （& s)**m_xFontNotification**初始化時**m_fontHeading**成員變數。  
  
 ![實作多個字型物件介面](../mfc/media/vc373q1.gif "vc373q1")  
實作多個字型物件介面  
  
 在上圖中實線顯示這兩個字型物件所使用的相同實作**IFontNotification**。 如果您想要在區別哪一種字型的變更，這可能會造成問題。  
  
 控制項的字型物件通知之間區別的一個方法是建立的不同實作**IFontNotification**控制項中每個字型物件介面。 這項技術可讓您藉由更新只有字串或字串，使用最近修改的字型的最佳化您的繪圖程式碼。 下列各節將示範實作第二個的字型屬性的個別通知介面所需的步驟。 第二個字型屬性會被假設為`HeadingFont`是在上一節中新增的屬性。  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a>實作新字型通知介面  
 若要區別兩個或多個字型的通知，新的通知介面必須實作每個控制項中所使用的字型。 下列章節說明如何藉由修改控制標頭和實作檔案中實作新字型告知介面。  
  
### <a name="additions-to-the-header-file"></a>標頭檔新增的項目  
 在控制項標頭檔 (。H），在類別宣告中加入下列幾行：  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 這會建立實作`IPropertyNotifySink`介面稱為`HeadingFontNotify`。 這個新介面包含方法呼叫`OnChanged`。  
  
### <a name="additions-to-the-implementation-file"></a>新增至實作檔  
 在標題中的字型 （控制建構函式） 的初始化程式碼變更`&m_xFontNotification`至`&m_xHeadingFontNotify`。 然後加入下列程式碼：  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 `AddRef`和`Release`方法`IPropertyNotifySink`追蹤的介面的 ActiveX 控制項物件的參考計數。 當控制項取得存取權的介面指標時，會呼叫控制項`AddRef`遞增參考計數。 當完成控制項時，指標時，它會呼叫`Release`，在很多相同的方式來**GlobalFree**可能呼叫來釋放全域記憶體區塊。 此介面的參考計數歸零時，就可以釋放介面實作。 在此範例中，`QueryInterface`函式會傳回指標`IPropertyNotifySink`特定物件上的介面。 此函式可讓查詢以判斷支援哪個介面物件的 ActiveX 控制項。  
  
 這些變更已對您的專案之後，重建專案，並使用測試容器測試該介面。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 在 ActiveX 控制項中使用圖片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)


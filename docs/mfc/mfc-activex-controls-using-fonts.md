---
title: "MFC ActiveX 控制項：使用字型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnFontChanged"
  - "HeadingFont"
  - "InternalFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字型, ActiveX 控制項"
  - "GetFont 方法"
  - "HeadingFont 屬性"
  - "InternalFont 方法"
  - "IPropertyNotifySink 類別"
  - "MFC ActiveX 控制項, 字型"
  - "告知, MFC ActiveX 控制項字型"
  - "OnDraw 方法, MFC ActiveX 控制項"
  - "OnFontChanged 方法"
  - "SelectStockFont 方法"
  - "SetFont 方法"
  - "內建字型屬性"
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC ActiveX 控制項：使用字型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果 ActiveX 控制項顯示文字，您可以允許使用者透過控制項變更字型屬性變更文字的外觀。  字型屬性會實作為字型物件，而且可以是兩種型別:內建或自訂。  內建字型屬性是事先實做您可以使用屬性精靈加入的字型屬性。  自訂字型屬性沒有 preimplemented，並由控制項開發人員決定屬性的行為和使用方式。  
  
 本章節涵蓋下列主題：  
  
-   [使用內建字型屬性](#_core_using_the_stock_font_property)  
  
-   [使用控制項的自訂字型屬性](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> 使用內建字型屬性  
 內建字型屬性由 [COleControl](../mfc/reference/colecontrol-class.md)類別 preimplemented。  此外，標準字型屬性頁也是可用，可讓使用者變更字型物件的各種屬性，例如名稱、大小和樣式。  
  
 透過 [GetFont](../Topic/COleControl::GetFont.md)、 [SetFont](../Topic/COleControl::SetFont.md)和 [InternalGetFont](../Topic/COleControl::InternalGetFont.md) 的 `COleControl`函式存取字型物件。  控制使用者透過 `GetFont` 來存取字型物件，以及與任何其他相同的 `SetFont` 函式取得\/設定屬性。  當對字型物件的存取需要從控制項的內部時，請使用 `InternalGetFont` 函式。  
  
 如 [MFC ActiveX 控制項:屬性](../mfc/mfc-activex-controls-properties.md)中所述，將內建屬性對 [加入屬性精靈](../ide/names-add-property-wizard.md)進行。  您選取的字型屬性，因此，加入屬性精靈會自動插入內建字型輸入控制項的分派對應。  
  
#### 使用屬性精靈，將內建字型屬性加入  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
     這樣會開啟 加入屬性精靈。  
  
5.  在**屬性名稱** 方塊中按一下 **字型**。  
  
6.  按一下 \[**完成**\]。  
  
 加入屬性精靈會將下列行加入至控制項的分派對應，位於控制項類別實作檔:  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_1.cpp)]  
  
 此外，加入屬性精靈會將下列行加入至控制項 .IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_2.idl)]  
  
 內建標頭屬性是使用內建字型屬性資訊，可以繪製文字屬性的範例。  將內建標頭屬性加入至控制項使用步驟類似於內建字型屬性的項目。  
  
#### 使用加入屬性精靈，將內建的標題屬性  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
     這樣會開啟 加入屬性精靈。  
  
5.  在 **Property Name** 方塊中，按一下 **Caption**。  
  
6.  按一下 \[**完成**\]。  
  
 加入屬性精靈會將下列行加入至控制項的分派對應，位於控制項類別實作檔:  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函式  
 `OnDraw` 的預設實作所顯示之任何文字使用 Windows 系統字型在控制項。  這表示您必須藉由選取字型物件修改 `OnDraw` 程式碼到裝置內容中。  如下列範例所示，若要這麼做，請呼叫 [COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md) 並傳遞控制裝置內容，例如:  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_4.cpp)]  
  
 在修改 `OnDraw` 函式使用 Font 物件後，控制項中的所有文字顯示於控制項內建字型屬性的特性。  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> 使用控制項的自訂字型屬性  
 除了內建字型屬性之外， ActiveX 控制項可能有自訂字型屬性。  若要將自訂字型屬性必須:  
  
-   使用加入屬性精靈會實作自訂字型屬性。  
  
-   [處理字型通知](#_core_processing_font_notifications)。  
  
-   [實作新的字型告知介面](#_core_implementing_a_new_font_notification_interface)。  
  
###  <a name="_core_implementing_a_custom_font_property"></a> 實作自訂字型屬性  
 若要實作自訂字型屬性，您可以使用加入屬性精靈會將屬性然後對程式碼進行修改。  下列章節描述如何將自訂 `HeadingFont` 屬性到範例控制項。  
  
##### 使用屬性精靈，將自訂字型屬性加入  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
     這樣會開啟 加入屬性精靈。  
  
5.  在 \[屬性名稱\] 方塊中輸入屬性的名稱。  在這個範例中使用  **HeadingFont**。  
  
6.  對於 **Implementation Type**，按一下 **Get\/Set Methods**。  
  
7.  在 **屬性型別** 方塊中，為屬性型別選取 **IDispatch\*** 。  
  
8.  按一下 \[**完成**\]。  
  
 加入屬性精靈會建立程式碼加入 `HeadingFont` 自訂屬性加入至 `CSampleCtrl` 類別和 SAMPLE.IDL 檔案。  因為 `HeadingFont` 是 Get\/Set 屬性型別，加入屬性精靈修改 `CSampleCtrl` 類別的分派對應包括 `DISP_PROPERTY_EX_ID`[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md) 巨集輸入:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_5.cpp)]  
  
 `DISP_PROPERTY_EX` 巨集相關聯 `HeadingFont` 的屬性名稱與其對應的 `CSampleCtrl` 類別 Get 和 Set 方法， `GetHeadingFont` 和 `SetHeadingFont`。  在這種情況下，也指定屬性值的型別，如**VT\_FONT**。  
  
 為了`GetHeadingFont` 和`SetHeadingFont`函式，加入屬性精靈也加入控制標頭檔案\(.H\)中宣告，並將函式樣板加入至控制項實作檔 \(.CPP\) :  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_6.cpp)]  
  
 最後，加入屬性精靈會將 `HeadingFont` 屬性的輸入修改控制 .IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_7.idl)]  
  
### 將程式碼修改至原始檔控制  
 現在您已將 `HeadingFont` 屬性設定為控制項，您必須對控制項標題和實作檔中進行變更完全支援新的屬性。  
  
 在控制項的標頭檔 \(.H\)，將受保護的成員變數的宣告:  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_8.h)]  
  
 在控制項實作檔 \(.CPP\)，請執行下列步驟:  
  
-   初始化控制項中建構函式的 `m_fontHeading` 。  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   宣告包含字型的預設屬性的靜態 **FONTDESC** 結構。  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   在 `DoPropExchange` 控制項的成員函式，請將呼叫 `PX_Font` 函式。  這對自訂字型屬性提供初始化並繼續。  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   實作控制 `GetHeadingFont` 成員函式的結束。  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   實作控制 `SetHeadingFont` 成員函式的結束。  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   修改控制項 `OnDraw` 成員函式定義變數會保留先前選取的字型。  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   修改控制項 `OnDraw` 成員函式選取這個自訂字型到裝置內容中將下列行位置，要使用的字型。  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   修改控制項 `OnDraw` 成員函式選取上字型回到裝置內容將下一行，在使用後字型。  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_16.cpp)]  
  
 在自訂字型屬性實作之後，應該實作標準字型屬性頁，可讓控制項在使用者變更控制項的目前字型。  若要加入標準字型屬性頁上的屬性頁 ID，請在 `BEGIN_PROPPAGEIDS` 巨集之後插入下列程式碼:  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_17.cpp)]  
  
 您必須也將 `BEGIN_PROPPAGEIDS` 巨集計數參數。  以下行數將說明這點：  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_18.cpp)]  
  
 在這些變更之後，請重建整個專案合併的功能。  
  
###  <a name="_core_processing_font_notifications"></a> 處理字型通知。  
 在大部分情況下需要知道何時變更字型物件的特性。  每個字型物件可以提供通知時，它會呼叫 **IFontNotification** 介面的成員函式變更時，實作 `COleControl`。  
  
 如果控制項使用內建字型屬性，其告知由 `COleControl`的 `OnFontChanged` 成員函式來處理。  當您將自訂字型屬性時，您可以讓它們使用相同的實作。  在本節中的範例中，會藉由傳遞&**m\_xFontNotification**將**m\_fontHeading**成員變數完成初始化時，完成。  
  
 ![實作多個字型物件介面](../mfc/media/vc373q1.png "vc373Q1")  
實作多個字型物件介面  
  
 在上圖顯示執行 \(由字型物件使用 **IFontNotification**的相同的實作。  如果字型變更您要差異，可能會造成問題。  
  
 一種方式區別控制項的字型物件告知之間會建立 **IFontNotification** 介面的不同實作每個字型物件的控制項。  這項技術可讓您藉由更新只有字串最佳化的繪圖程式碼或資料，使用最近修改的字型。  下列區段顯示的必要步驟實作第二個字型屬性的不同告知介面。  第二個字型屬性假設是上一節中加入的 `HeadingFont` 屬性。  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> 實作新的字型告知介面。  
 若要區別兩個或多個字型的告知之間，必須針對每個控制項的字型實作新的介面。  下列章節說明如何透過修改控制項標題和實作檔實作新的字型告知介面。  
  
### 對標頭檔的時機  
 在控制項的標頭檔 \(.H\)，加入下列程式碼加入至類別宣告:  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_19.h)]  
  
 這建立名為`HeadingFontNotify`的`IPropertyNotifySink`介面實做。  這個介面包含呼叫 `OnChanged`的方法。  
  
### 對實作檔案加入  
 在初始化標題字型的程式碼 \(控制項建構函式\)，請將 `&m_xFontNotification` 變更為 `&m_xHeadingFontNotify`。  將下列程式碼加入至:  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_20.cpp)]  
  
 在 `IPropertyNotifySink` 介面的 `AddRef` 和 `Release` 方法記錄 ActiveX 控制項物件的參考計數。  當控制項取得對介面指標時，控制項會呼叫 `AddRef` 將參考次數 \(Reference Count\)。  當控制項與指標時，它會呼叫 `Release`，以相同方式 **GlobalFree** 可能呼叫釋放全域記憶體區塊。  當這個介面的參考次數移至零時，介面實作可以被釋放。  在此範例中， `QueryInterface` 函式會傳回指標在特定物件的 `IPropertyNotifySink` 介面。  這個函式允許 ActiveX 控制項查詢物件判斷介面支援它。  
  
 在這些變更專案之後，請重新建置專案並使用測試容器測試介面。  如需存取測試容器的詳細資訊，請參閱[用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)
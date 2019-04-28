---
title: MFC ActiveX 控制項：加入內建屬性
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 940f61c9ce6ccb57843333582455e61c1f7ac73b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225339"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控制項：加入內建屬性

內建屬性與不同的自訂屬性的類別已實作`COleControl`。 `COleControl` 包含支援控制項的通用屬性的預先定義的成員函式。 某些常見的屬性包含控制項的標題和前景和背景色彩。 如需其他內建的屬性資訊，請參閱[加入屬性精靈 所支援的內建屬性](#_core_stock_properties_supported_by_classwizard)本文稍後。 內建屬性一律會加 DISP_STOCKPROP 分派對應項目。

這篇文章描述如何將 ActiveX 控制項，使用 [新增屬性精靈] 中的內建的屬性 （在此案例中，標題），並說明產生的程式碼修改。 主題包括：

- [使用 [新增屬性精靈] 將內建屬性](#_core_using_classwizard_to_add_a_stock_property)

- [加入屬性精靈變更內建屬性](#_core_classwizard_changes_for_stock_properties)

- [加入屬性精靈 所支援的內建屬性](#_core_stock_properties_supported_by_classwizard)

- [內建屬性和通知](#_core_stock_properties_and_notification)

- [色彩屬性](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 自訂控制項通常會有屬性，例如頂端、 左邊、 寬度、 高度、 Align、 標記、 名稱、 TabIndex、 定位點和父代。 ActiveX 控制項容器，不過，要負責實作這些控制項的屬性，因此 ActiveX 控制項應支援這些屬性。

##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用加入屬性精靈來加入內建屬性

加入內建屬性必須比新增自訂屬性，因為較少程式碼支援的屬性會自動處理`COleControl`。 下列程序示範如何將庫存 Caption 屬性對 ActiveX 控制項架構，並也可用來新增其他內建的屬性。 取代標題為選取的內建屬性名稱。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要新增內建的 Caption 屬性使用 加入屬性精靈

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

   這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。

1. 在 **屬性名稱**方塊中，按一下**標題**。

1. 按一下 [ **完成**]。

##  <a name="_core_classwizard_changes_for_stock_properties"></a> 加入屬性精靈針對變更內建屬性

因為`COleControl`支援內建屬性，加入屬性精靈不會變更以任何方式在類別宣告，它將屬性新增至分派對應。 加入屬性精靈 將下面這一行加入至控制項，其位於實作的分派對應 (。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

下面這一行新增至您的控制項介面的描述 (。IDL) 檔：

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

這一行會指派 Caption 屬性特定的識別碼。 請注意，屬性是可繫結，而且會向資料庫要求的權限之前修改值。

這會 Caption 屬性提供給控制項的使用者。 若要使用的內建屬性的值，可存取的成員變數或成員函式`COleControl`基底類別。 如需有關這些成員變數和成員函式的詳細資訊，請參閱下一步 區段中，加入屬性精靈 所支援的內建屬性。

##  <a name="_core_stock_properties_supported_by_classwizard"></a> 內建支援的屬性加入屬性精靈

`COleControl`類別提供九個內建的屬性。 您可以新增想要使用 [新增屬性精靈] 的屬性。

|屬性|分派對應項目|如何存取值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE( )|值為可存取`m_sAppearance`。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR( )|值，藉由呼叫可存取`GetBackColor`。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE( )|值為可存取`m_sBorderStyle`。|
|`Caption`|DISP_STOCKPROP_CAPTION( )|值，藉由呼叫可存取`InternalGetText`。|
|`Enabled`|DISP_STOCKPROP_ENABLED( )|值為可存取`m_bEnabled`。|
|`Font`|DISP_STOCKPROP_FONT( )|請參閱文章[MFC ActiveX 控制項：使用字型](../mfc/mfc-activex-controls-using-fonts.md)使用量。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR( )|值，藉由呼叫可存取`GetForeColor`。|
|`hWnd`|DISP_STOCKPROP_HWND （)|值為可存取`m_hWnd`。|
|`Text`|DISP_STOCKPROP_TEXT( )|值，藉由呼叫可存取`InternalGetText`。 這個屬性等同於`Caption`，除了屬性的名稱。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|值為可存取`m_lReadyState`或 `GetReadyState`|

##  <a name="_core_stock_properties_and_notification"></a> 內建屬性和通知

大部分的內建屬性具有可覆寫通知函式。 例如，每當`BackColor`屬性變更時，`OnBackColorChanged`呼叫函式 （控制項類別的成員函式）。 預設實作 (在`COleControl`) 呼叫`InvalidateControl`。 如果您想要以這種情況的回應採取其他動作，請覆寫這個函式。

##  <a name="_core_color_properties"></a> 色彩屬性

您可以使用股票`ForeColor`和`BackColor`屬性或您自己的自訂色彩屬性，繪製控制項時。 若要使用的色彩屬性，呼叫[COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor)成員函式。 此函式的參數是 color 屬性和選用的調色盤控制代碼的值。 傳回值是**COLORREF**值，可以傳遞至 GDI 函式，例如`SetTextColor`和`CreateSolidBrush`。

內建的色彩值`ForeColor`並`BackColor`藉由呼叫其中一個存取屬性`GetForeColor`或`GetBackColor`分別函式。

下列範例示範如何使用這些兩個色彩屬性，繪製控制項時。 它會初始化暫存**COLORREF**變數並`CBrush`呼叫的物件`TranslateColor`： 另一種使用`ForeColor`屬性和其他使用`BackColor`屬性。 暫存`CBrush`物件會被用來繪製控制項的矩形，並使用設定的文字色彩`ForeColor`屬性。

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

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
ms.openlocfilehash: 13e8af5ddb3dd5130c864e42383e3bb9ff23b87b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625430"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控制項：加入內建屬性

內建屬性與自訂屬性不同之處在于，它們已經由類別實作為 `COleControl` 。 `COleControl`包含預先定義的成員函式，這些函式支援控制項的通用屬性。 某些常見的屬性包括控制項的標題和前景和背景色彩。 如需其他內建屬性的詳細資訊，請參閱本文稍後[的「新增屬性嚮導」所支援的](#_core_stock_properties_supported_by_classwizard)內建屬性。 庫存屬性的分派對應專案一律會加上 DISP_STOCKPROP。

本文說明如何使用 [加入屬性] Wizard 將內建屬性（在此案例中為標題）新增至 ActiveX 控制項，並說明產生的程式碼修改。 主題包括：

- [使用 [新增屬性] Wizard 來加入內建屬性](#_core_using_classwizard_to_add_a_stock_property)

- [加入庫存屬性的屬性 Wizard 變更](#_core_classwizard_changes_for_stock_properties)

- [新增屬性 Wizard 支援的內建屬性](#_core_stock_properties_supported_by_classwizard)

- [庫存屬性和通知](#_core_stock_properties_and_notification)

- [色彩屬性](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 自訂控制項通常具有 Top、Left、Width、Height、Align、Tag、Name、TabIndex、TabStop 和 Parent 等屬性。 不過，ActiveX 控制項容器會負責執行這些控制項屬性，因此 ActiveX 控制項不應支援這些屬性。

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>使用 [新增屬性] Wizard 來加入內建屬性

加入內建屬性所需的程式碼比加入自訂屬性少，因為會自動處理屬性的支援 `COleControl` 。 下列程式示範如何將 [內建標題] 屬性加入至 ActiveX 控制項架構，也可以用來加入其他的內建屬性。 以選取的庫存屬性名稱取代標題。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要使用加入屬性 Wizard 加入股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

   這會開啟 [[新增屬性] Wizard](../ide/names-add-property-wizard.md)。

1. 在 [**屬性名稱**] 方塊中，按一下 [**標題**]。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>加入庫存屬性的屬性 Wizard 變更

因為 `COleControl` 支援內建屬性，所以 [加入屬性] Wizard 不會以任何方式變更類別宣告，而是將屬性新增至分派對應。 [加入屬性] Wizard 會將下列這一行新增至控制項的分派對應，該圖位於執行中（。CPP）檔案：

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

下面這一行會加入至控制項的介面描述（。IDL）檔案：

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

這一行會為標題屬性指派特定的識別碼。 請注意，此屬性是可系結的，並且會在修改值之前要求資料庫的許可權。

這會讓標題屬性可供控制項的使用者使用。 若要使用 stock 屬性的值，請存取基類的成員變數或成員函式 `COleControl` 。 如需這些成員變數和成員函式的詳細資訊，請參閱下一節「新增屬性嚮導」所支援的內建屬性。

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>新增屬性 Wizard 支援的內建屬性

`COleControl`類別提供九個內建屬性。 您可以使用 [新增屬性] Wizard 來新增您想要的屬性。

|屬性|分派對應專案|如何存取值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE （）|可存取的值 `m_sAppearance` 。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR （）|呼叫可存取的值 `GetBackColor` 。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE （）|可存取的值 `m_sBorderStyle` 。|
|`Caption`|DISP_STOCKPROP_CAPTION （）|呼叫可存取的值 `InternalGetText` 。|
|`Enabled`|DISP_STOCKPROP_ENABLED （）|可存取的值 `m_bEnabled` 。|
|`Font`|DISP_STOCKPROP_FONT （）|請參閱[MFC ActiveX 控制項：使用](mfc-activex-controls-using-fonts.md)字型來取得使用方式一文。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR （）|呼叫可存取的值 `GetForeColor` 。|
|`hWnd`|DISP_STOCKPROP_HWND （）|可存取的值 `m_hWnd` 。|
|`Text`|DISP_STOCKPROP_TEXT （）|呼叫可存取的值 `InternalGetText` 。 `Caption`除了屬性名稱以外，這個屬性與相同。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE （）|可存取為 `m_lReadyState` 或的值`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>庫存屬性和通知

大部分的內建屬性都有可覆寫的通知函數。 例如，每當 `BackColor` 屬性變更時， `OnBackColorChanged` 就會呼叫函式（控制項類別的成員函式）。 預設的實作為 `COleControl` 呼叫 `InvalidateControl` 。 如果您想要採取其他動作來回應這種情況，請覆寫此函數。

## <a name="color-properties"></a><a name="_core_color_properties"></a>色彩屬性

繪製控制項時，您可以使用 [內建] `ForeColor` 和 [ `BackColor` 屬性]，或您自己的自訂色彩屬性。 若要使用 color 屬性，請呼叫[COleControl：： TranslateColor](reference/colecontrol-class.md#translatecolor)成員函式。 此函式的參數是 color 屬性的值和選擇性的調色板控制碼。 傳回值是可以傳遞給 GDI 函數的**COLORREF**值，例如 `SetTextColor` 和 `CreateSolidBrush` 。

您可以 `ForeColor` 分別呼叫或函式，以存取股票和屬性的色彩值 `BackColor` `GetForeColor` `GetBackColor` 。

下列範例示範在繪製控制項時，使用這兩個色彩屬性。 它會使用屬性**COLORREF** （property） `CBrush` `TranslateColor` 和另一個使用屬性的呼叫，初始化暫存 COLORREF 變數和物件 `ForeColor` `BackColor` 。 `CBrush`接著會使用暫存物件繪製控制項的矩形，並使用屬性來設定文字色彩 `ForeColor` 。

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)

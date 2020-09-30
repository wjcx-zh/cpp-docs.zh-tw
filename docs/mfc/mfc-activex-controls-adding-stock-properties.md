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
ms.openlocfilehash: 27fed55ac8a5fc8b95f81c1bfd2c6edb3da6227d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502241"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控制項：加入內建屬性

內建屬性與自訂屬性不同之處在于，它們已經由類別所執行 `COleControl` 。 `COleControl` 包含支援控制項通用屬性的預先定義成員函式。 某些常見的屬性包括控制項的標題、前景和背景色彩。 如需其他內建屬性的詳細資訊，請參閱本文稍後 [的 [新增屬性] 嚮導所支援的庫存屬性](#_core_stock_properties_supported_by_classwizard) 。 內建屬性的分派對應專案一律會以 DISP_STOCKPROP 的首碼。

本文說明如何在此案例中加入內建屬性 (在此案例中，使用 [加入屬性] Wizard 將標題) 至 ActiveX 控制項，並說明產生的程式碼修改。 主題包括：

- [使用新增屬性 Wizard 加入內建屬性](#_core_using_classwizard_to_add_a_stock_property)

- [新增內建屬性的屬性 Wizard 變更](#_core_classwizard_changes_for_stock_properties)

- [[新增屬性] Wizard 支援的股票屬性](#_core_stock_properties_supported_by_classwizard)

- [庫存屬性和通知](#_core_stock_properties_and_notification)

- [色彩屬性](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 自訂控制項一般都有屬性，例如 Top、Left、Width、Height、Align、Tag、Name、TabIndex、TabStop 和 Parent。 但是 ActiveX 控制項容器會負責執行這些控制項屬性，因此 ActiveX 控制項不應支援這些屬性。

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用新增屬性 Wizard 加入內建屬性

加入內建屬性需要較少的程式碼，而不是加入自訂屬性，因為會自動處理屬性的支援 `COleControl` 。 下列程式示範如何將股票字幕屬性加入至 ActiveX 控制項架構，也可以用來加入其他內建屬性。 以所選取的內建屬性名稱取代標題。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用新增屬性 Wizard 來新增股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入屬性**]。

   這會開啟 [ [加入屬性] Wizard](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)。

1. 在 [ **屬性名稱** ] 方塊中，按一下 [ **標題**]。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a> 新增內建屬性的屬性 Wizard 變更

因為 `COleControl` 支援內建屬性，所以 [加入屬性] Wizard 不會以任何方式變更類別宣告，而會將屬性新增至分派對應。 [新增屬性] Wizard 會將下列這一行加入至控制項的分派對應中，該控制項位於 [執行 (] 中。CPP) 檔案：

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

下一行會加入至控制項的介面描述 (。IDL) 檔案：

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

這一行會將特定識別碼指派給 Caption 屬性。 請注意，此屬性是可系結的，並且會在修改值之前要求資料庫的許可權。

這會讓標題屬性可供您的控制項的使用者使用。 若要使用內建屬性的值，請存取基類的成員變數或成員函式 `COleControl` 。 如需有關這些成員變數和成員函式的詳細資訊，請參閱下一節：加入屬性 Wizard 所支援的內建屬性。

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a> [新增屬性] Wizard 支援的股票屬性

`COleControl`類別提供九個股票屬性。 您可以使用 [加入屬性] Wizard 來加入您想要的屬性。

|屬性|分派對應專案|如何存取值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE ( ) |可存取的值為 `m_sAppearance` 。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR ( ) |藉由呼叫來存取值 `GetBackColor` 。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE ( ) |可存取的值為 `m_sBorderStyle` 。|
|`Caption`|DISP_STOCKPROP_CAPTION ( ) |藉由呼叫來存取值 `InternalGetText` 。|
|`Enabled`|DISP_STOCKPROP_ENABLED ( ) |可存取的值為 `m_bEnabled` 。|
|`Font`|DISP_STOCKPROP_FONT ( ) |請參閱 [MFC ActiveX 控制項：使用](mfc-activex-controls-using-fonts.md) 字型提供使用方式一文。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR ( ) |藉由呼叫來存取值 `GetForeColor` 。|
|`hWnd`|DISP_STOCKPROP_HWND ( ) |可存取的值為 `m_hWnd` 。|
|`Text`|DISP_STOCKPROP_TEXT ( ) |藉由呼叫來存取值 `InternalGetText` 。 這個屬性與 `Caption` 屬性名稱不同，但屬性名稱除外。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE ( # A1|以或形式存取的值 `m_lReadyState``GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a> 庫存屬性和通知

大部分的內建屬性都有可覆寫的通知函數。 例如，每當 `BackColor` 屬性變更時， `OnBackColorChanged` 就會呼叫) 的控制項類別成員函式 (函式。 ) 呼叫中的預設實 (`COleControl` `InvalidateControl` 。 如果您想要採取其他動作來回應這種情況，請覆寫此函數。

## <a name="color-properties"></a><a name="_core_color_properties"></a> 色彩屬性

繪製控制項時，您可以使用股票 `ForeColor` 和 `BackColor` 屬性，或您自己的自訂色彩屬性。 若要使用 color 屬性，請呼叫 [COleControl：： TranslateColor](reference/colecontrol-class.md#translatecolor) 成員函式。 這個函式的參數是 color 屬性的值和選擇性的調色板控制碼。 傳回值是可傳遞給 GDI 函數的 **COLORREF** 值，例如 `SetTextColor` 和 `CreateSolidBrush` 。

您可以 `ForeColor` `BackColor` 分別呼叫或函數來存取 stock 和屬性的色彩值 `GetForeColor` `GetBackColor` 。

下列範例示範在繪製控制項時，如何使用這兩個色彩屬性。 它會初始化暫存 **COLORREF** 變數和 `CBrush` 具有呼叫的物件 `TranslateColor` ：一個使用 `ForeColor` 屬性，另一個是使用 `BackColor` 屬性。 `CBrush`接著會使用暫存物件來繪製控制項的矩形，並使用屬性設定文字色彩 `ForeColor` 。

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)

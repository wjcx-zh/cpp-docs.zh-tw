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
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364667"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控制項：加入內建屬性

股票屬性與自定義屬性不同,因為它們已由類`COleControl`實現。 `COleControl`包含支援控制項的通用屬性的預定義成員函數。 一些常見屬性包括控制項的標題以及前景和背景顏色。 有關其他股票屬性的資訊,請參閱本文後面的[添加屬性精靈支援的股票屬性](#_core_stock_properties_supported_by_classwizard)。 股票屬性的調度映射條目始終由DISP_STOCKPROP來預定。

本文介紹如何使用添加屬性嚮導將股票屬性(本例中為標題)添加到 ActiveX 控件,並解釋生成的代碼修改。 主題包括：

- [使用新增屬性精靈加入股票屬性](#_core_using_classwizard_to_add_a_stock_property)

- [新增股票屬性的屬性精靈變更](#_core_classwizard_changes_for_stock_properties)

- [新增屬性精靈支援的股票屬性](#_core_stock_properties_supported_by_classwizard)

- [庫存屬性和通知](#_core_stock_properties_and_notification)

- [色彩屬性](#_core_color_properties)

    > [!NOTE]
    >  可視化基本自定義控制項通常具有諸如「頂部」、「左側」、「寬度」、「高度」、「對齊」、「標記」、「名稱」、「TabIndex」、「TabStop」和「父級」等屬性。 但是,ActiveX 控制容器負責實現這些控制屬性,因此 ActiveX 控件不應支援這些屬性。

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>使用「新增屬性精靈」新增股票屬性

新增股票屬性需要的代碼比新增自訂屬性少,因為對屬性的支援由 自動`COleControl`處理 。 以下過程演示了將股票標題屬性添加到 ActiveX 控制件框架,還可用於添加其他股票屬性。 將所選股票屬性名稱替換為標題。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用新增屬性精靈加入股票標題屬性

1. 載入控制項專案。

1. 在 [類別檢視] 中，展開控制項的程式庫節點。

1. 在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。

1. 在快捷選單中,按一下「**添加**」,然後按下「**添加屬性**」 。。

   這會開啟[新增屬性精靈](../ide/names-add-property-wizard.md)。

1. 在 **「屬性名稱」** 框中,按下 **「標題**」。

1. 按一下 [完成] 。

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>新增股票屬性的屬性精靈變更

由於`COleControl`支援股票屬性,因此添加屬性嚮導不會以任何方式更改類聲明;因此,不會更改類聲明。它將屬性添加到調度映射。 "添加屬性精靈"將以下行添加到位於實現 (的控制件的調度映射中)。CPP) 檔案:

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

以下行將添加到控件的介面說明 (。IDL) 檔案:

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

此行為標題屬性分配特定 ID。 請注意,該屬性是可綁定的,將在修改值之前從資料庫請求許可權。

這使標題屬性可供控制項的使用者使用。 要使用 stock 屬性的值,`COleControl`請使用 基類的成員變數或成員函數。 有關這些成員變數和成員函數的詳細資訊,請參閱下一節"添加屬性嚮導支援的股票屬性"。

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>新增屬性精靈支援的股票屬性

該`COleControl`類提供九個股票屬性。 您可以使用「添加屬性嚮導」 添加所需的屬性。

|屬性|排程對應項目|如何存取值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE)|值可存`m_sAppearance`取為 。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR)|可通過調用`GetBackColor`訪問的值。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE)|值可存`m_sBorderStyle`取為 。|
|`Caption`|DISP_STOCKPROP_CAPTION)|可通過調用`InternalGetText`訪問的值。|
|`Enabled`|DISP_STOCKPROP_ENABLED)|值可存`m_bEnabled`取為 。|
|`Font`|DISP_STOCKPROP_FONT( )|請參閱文章[MFC ActiveX 控制件:使用字體](../mfc/mfc-activex-controls-using-fonts.md)進行使用。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR)|可通過調用`GetForeColor`訪問的值。|
|`hWnd`|DISP_STOCKPROP_HWND)|值可存`m_hWnd`取為 。|
|`Text`|DISP_STOCKPROP_TEXT)|可通過調用`InternalGetText`訪問的值。 此屬性與`Caption`相同,屬性名稱除外。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|值可存`m_lReadyState`取或或`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>股票屬性和通知

大多數股票屬性具有可以重寫的通知函數。 例如,每當更改`BackColor`屬性時,`OnBackColorChanged`都會調用函數(控件類的成員函數)。 預設實現 (`COleControl`在`InvalidateControl`) 呼叫 。 如果要針對此情況執行其他操作,請重寫此函數。

## <a name="color-properties"></a><a name="_core_color_properties"></a>色彩屬性

繪製控制項時,可以使用`ForeColor`股票`BackColor`和屬性或您自己的自訂顏色屬性。 要使用顏色屬性,請調用[COleControl::翻譯顏色](../mfc/reference/colecontrol-class.md#translatecolor)成員函數。 此函數的參數是顏色屬性的值和可選的調色板句柄。 傳回值是一個**COLORREF**值,可以傳遞給 GDI 函數,`SetTextColor`如`CreateSolidBrush`與 。

`ForeColor`通過分別調用`BackColor``GetForeColor``GetBackColor`或 函數來存取股票和屬性的顏色值。

下面的示例演示了在繪製控件時使用這兩個顏色屬性。 它初始化暫時的**COLORREF**變數`CBrush`和一個物件`TranslateColor`, 其中一`ForeColor`個使用 屬性呼`BackColor`叫 ,另一個使用 屬性。 然後,`CBrush`暫時物件用於繪製控制的矩形,並使用`ForeColor`屬性設定文字顏色。

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

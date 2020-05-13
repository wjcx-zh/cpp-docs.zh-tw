---
title: MFC ActiveX 控制項：屬性頁
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364573"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控制項：屬性頁

屬性頁允許 ActiveX 控制件使用者查看和更改 ActiveX 控制件屬性。 這些屬性是透過調用控制項屬性對話框來存取的,該對話方塊包含一個或多個屬性頁,這些頁面提供用於查看和編輯控制項屬性的自訂圖形介面。

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

ActiveX 控制項屬性頁以兩種方式顯示:

- 呼叫控制項的屬性「謂詞 **(OLEIVERB_PROPERTIES**)時,控制項將打開一個包含控制式屬性頁的模式屬性對話框。

- 容器可以顯示其自己的無模式對話框,該對話框顯示所選控件的屬性頁。

屬性對話框(下圖所示)包括用於顯示當前屬性頁的區域、用於在屬性頁之間切換的選項卡以及執行常見任務的按鈕的集合,如關閉屬性頁對話框、取消所做的任何更改或立即對 ActiveX 控件應用任何更改。

![Circ3 的屬性對話方塊](../mfc/media/vc373i1.gif "Circ3 的屬性對話方塊") <br/>
內容對話方塊

本文介紹與在 ActiveX 控件中使用屬性頁相關的主題。 其中包括：

- [將 ActiveX 控制檔的預設屬性頁](#_core_implementing_the_default_property_page)

- [新增控制檔到屬性頁](#_core_adding_controls_to_a_property_page)

- [自訂 DoDataExchange 功能](#_core_customizing_the_dodataexchange_function)

有關在 ActiveX 控制件中使用屬性頁的詳細資訊,請參閱以下文章:

- [MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

有關在 MFC 應用程式中使用屬性表(而不是 ActiveX 控制件)的資訊,請參閱[屬性表](../mfc/property-sheets-mfc.md)。

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>設定預設屬性頁

如果使用 ActiveX 控件精靈建立控制項專案,則 ActiveX 控制項精靈為派生自[COlePropertyPage 類](../mfc/reference/colepropertypage-class.md)的控制項提供預設屬性頁類。 最初,此屬性頁為空,但您可以將任何對話方塊控制項或控制項集添加到其中。 由於 ActiveX 控制件精靈預設情況下只創建一個屬性頁類,因此必須使用 類視`COlePropertyPage`圖創建 其他屬性頁類(也派生自 )。 有關此過程的詳細資訊,請參閱[MFC ActiveX 控制件:新增另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。

設定屬性頁(本例為預設值)是一個三步過程:

#### <a name="to-implement-a-property-page"></a>設定屬性頁

1. 向控件`COlePropertyPage`專案添加派生類。 如果專案是使用 ActiveX 控制件精靈建立的(如本例),則預設屬性頁類已存在。

1. 使用對話框編輯器將任何控制項添加到屬性頁範本。

1. `DoDataExchange`自定義`COlePropertyPage`派生類的功能以在屬性頁控件和 ActiveX 控制項之間交換值。

例如,以下過程使用簡單的控制項(稱為"範例")。 範例是使用 ActiveX 控制件精靈建立的,並且僅包含庫存標題屬性。

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>新增控制檔到屬性頁

#### <a name="to-add-controls-to-a-property-page"></a>新增屬性頁加入控制項

1. 打開控制專案后,打開資源檢視。

1. 按兩下 **「對話框**」目錄圖示。

1. 打開IDD_PROPPAGE_SAMPLE對話方塊。

   ActiveX 控制精靈將專案的名稱追加到對話框 ID 的末尾,本例中為範例。

1. 將所選控制件從「工具箱」拖放到對話框區域。

1. 此選項,文字標籤控制件標題與具有IDC_CAPTION識別碼的編輯框控制項就足夠了。

1. 按下「在工具列上**保存**」以儲存更改。

現在使用者介面已被修改,您需要將編輯框與"標題"屬性連結。 這通過編輯`CSamplePropPage::DoDataExchange`函數在以下部分完成。

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>自訂 DoData 交換功能

屬性頁[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)函數允許您將屬性頁值與控制項中屬性的實際值連結。 要建立連結,必須將相應的屬性頁欄位映射到其各自的控制項屬性。

這些映射使用屬性頁**DDP_** 函數實現。 **DDP_** 函數的工作方式與標準 MFC 對話框中使用的**DDX_** 函數類似,但有一個例外。 除了對成員變數的引用外 **,DDP_** 函數採用控制項屬性的名稱。 以下是屬性頁函數中`DoDataExchange`的典型條目。

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函數使用`DDP_TEXT`函數將屬性頁的*m_caption*成員變數與標題關聯。

插入屬性頁控制項後,需要使用上述`DDP_Text`函數在屬性頁控制件、IDC_CAPTION和實際控制項屬性"Caption"之間建立連結。

[屬性頁](../mfc/reference/property-pages-mfc.md)可用於其他對話方塊控制項類型,如複選框、單選按鈕和清單框。 下表列出了函數**DDP_** 及其用途的整組屬性頁:

### <a name="property-page-functions"></a>屬性頁函數

|函式名稱|使用此函式連結|
|-------------------|-------------------------------|
|`DDP_CBIndex`|組合框中所選字串的索引具有控制項屬性。|
|`DDP_CBString`|組合框中的選定字串具有控制項屬性。 所選字串可以以與屬性值相同的字母開頭,但不必完全匹配它。|
|`DDP_CBStringExact`|組合框中的選定字串具有控制項屬性。 所選字串和屬性的字串值必須完全匹配。|
|`DDP_Check`|具有控制項屬性的複選框。|
|`DDP_LBIndex`|具有控制項屬性的清單框中的選擇字串索引。|
|`DDP_LBString`|具有控制項屬性的清單框中的選擇字串。 所選字串可以以與屬性值相同的字母開頭,但不必完全匹配它。|
|`DDP_LBStringExact`|具有控制項屬性的清單框中的選擇字串。 所選字串和屬性的字串值必須完全匹配。|
|`DDP_Radio`|具有控制屬性的單選按鈕。|
|`DDP_Text`|具有控制項屬性的文字。|

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage 類別](../mfc/reference/colepropertypage-class.md)

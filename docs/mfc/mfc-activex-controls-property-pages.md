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
ms.openlocfilehash: 3d22085daa503a7c778111718445920f98b98a89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615433"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控制項：屬性頁

屬性頁可讓 ActiveX 控制項使用者查看和變更 ActiveX 控制項屬性。 藉由叫用 [控制項屬性] 對話方塊，即可存取這些屬性，其中包含一或多個屬性頁，可提供自訂的圖形介面來用來查看和編輯控制項屬性。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

ActiveX 控制項屬性頁的顯示方式有兩種：

- 叫用控制項的 Properties 動詞（**OLEIVERB_PROPERTIES**）時，控制項會開啟一個包含控制項屬性頁的模式屬性對話方塊。

- 容器可以顯示自己的非強制回應對話方塊，以顯示所選控制項的屬性頁。

[屬性] 對話方塊（如下圖所示）包含一個區域，用來顯示目前的屬性頁、在屬性頁之間切換的索引標籤，以及執行一般工作（例如關閉屬性頁對話方塊、取消任何變更，或立即將任何變更套用至 ActiveX 控制項）的按鈕集合。

![Circ3 的屬性對話方塊](../mfc/media/vc373i1.gif "Circ3 的屬性對話方塊") <br/>
內容對話方塊

本文涵蓋在 ActiveX 控制項中使用屬性頁的相關主題。 它們包括：

- [執行 ActiveX 控制項的預設屬性頁](#_core_implementing_the_default_property_page)

- [將控制項加入至屬性頁](#_core_adding_controls_to_a_property_page)

- [自訂 DoDataExchange 函式](#_core_customizing_the_dodataexchange_function)

如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：加入另一個自訂屬性頁](mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控制項：使用內建屬性頁](mfc-activex-controls-using-stock-property-pages.md)

如需在 ActiveX 控制項以外的 MFC 應用程式中使用屬性工作表的詳細資訊，請參閱[屬性工作表](property-sheets-mfc.md)。

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>執行預設屬性頁

如果您使用 ActiveX Control Wizard 來建立控制項專案，ActiveX 控制項 Wizard 會為衍生自[COlePropertyPage 類別](reference/colepropertypage-class.md)的控制項提供預設的屬性頁類別。 一開始，這個屬性頁是空白的，但您可以在其中加入任何對話方塊控制項或控制項集合。 因為 ActiveX 控制項嚮導預設只會建立一個屬性頁類別，所以 `COlePropertyPage` 必須使用類別檢視來建立其他屬性頁類別（也衍生自）。 如需此程式的詳細資訊，請參閱[MFC ActiveX 控制項：加入另一個自訂屬性頁](mfc-activex-controls-adding-another-custom-property-page.md)。

執行屬性頁（在此案例中為預設值）是三個步驟的程式：

#### <a name="to-implement-a-property-page"></a>若要執行屬性頁

1. 將 `COlePropertyPage` 衍生類別加入至控制項專案。 如果專案是使用 ActiveX Control Wizard 建立的（如本例所示），則預設的屬性頁類別已經存在。

1. 使用對話方塊編輯器，將任何控制項加入至屬性頁範本。

1. 自訂 `DoDataExchange` `COlePropertyPage` 衍生類別的函式，以交換屬性頁控制項和 ActiveX 控制項之間的值。

例如，下列程式會使用簡單的控制項（名為「範例」）。 範例是使用 ActiveX Control Wizard 建立的，而且只包含 stock Caption 屬性。

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>將控制項加入至屬性頁

#### <a name="to-add-controls-to-a-property-page"></a>若要將控制項加入至屬性頁

1. 在開啟控制項專案的情況下，開啟資源檢視。

1. 按兩下 [對話方塊目錄 **]** 圖示。

1. 開啟 [IDD_PROPPAGE_SAMPLE] 對話方塊。

   ActiveX 控制項 Wizard 會將專案名稱附加至對話方塊識別碼的結尾，在此範例中為 Sample。

1. 將選取的控制項從 [工具箱] 拖放至對話方塊區域。

1. 在此範例中，文字標籤控制項「標題：」和具有 IDC_CAPTION 識別碼的編輯方塊控制項就已足夠。

1. 按一下工具列上的 [**儲存**] 來儲存您的變更。

現在已修改使用者介面，您必須使用 [標題] 屬性來連結編輯方塊。 這會在下一節中編輯函數來完成 `CSamplePropPage::DoDataExchange` 。

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>自訂 DoDataExchange 函式

您的屬性頁[CWnd：:D odataexchange](reference/cwnd-class.md#dodataexchange)函數可讓您將屬性頁值與控制項中屬性的實際值連結。 若要建立連結，您必須將適當的屬性頁欄位對應到其各自的控制項屬性。

這些對應會使用屬性頁**DDP_** 函數來執行。 **DDP_** 函式的運作方式類似于標準 MFC 對話方塊中所使用的**DDX_** 函式，但有一個例外狀況。 除了成員變數的參考之外， **DDP_** 函式會採用控制項屬性的名稱。 以下是屬性頁的函式中的一般專案 `DoDataExchange` 。

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函式會使用函數，將屬性頁的*m_caption*成員變數與標題產生關聯 `DDP_TEXT` 。

插入屬性頁控制項之後，您必須使用上述的函式，在屬性頁控制項、IDC_CAPTION 和實際控制項屬性（Caption）之間建立連結 `DDP_Text` 。

[屬性頁](reference/property-pages-mfc.md)適用于其他對話方塊控制項類型，例如核取方塊、選項按鈕和清單方塊。 下表列出整組屬性頁**DDP_** 函式及其用途：

### <a name="property-page-functions"></a>屬性頁函式

|函式名稱|使用此函數連結|
|-------------------|-------------------------------|
|`DDP_CBIndex`|下拉式方塊中具有控制項屬性的選取字串索引。|
|`DDP_CBString`|下拉式方塊中具有控制項屬性的選取字串。 選取的字串開頭必須與屬性的值相同，但不需要完全相符。|
|`DDP_CBStringExact`|下拉式方塊中具有控制項屬性的選取字串。 選取的字串和屬性的字串值必須完全相符。|
|`DDP_Check`|具有控制項屬性的核取方塊。|
|`DDP_LBIndex`|具有控制項屬性的清單方塊中選取的字串索引。|
|`DDP_LBString`|清單方塊中具有控制項屬性的選取字串。 選取的字串開頭必須與屬性的值相同，但不需要完全相符。|
|`DDP_LBStringExact`|清單方塊中具有控制項屬性的選取字串。 選取的字串和屬性的字串值必須完全相符。|
|`DDP_Radio`|具有控制項屬性的選項按鈕。|
|`DDP_Text`|具有控制項屬性的文字。|

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[COlePropertyPage 類別](reference/colepropertypage-class.md)

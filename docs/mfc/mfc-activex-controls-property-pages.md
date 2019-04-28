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
ms.openlocfilehash: 3fe092e412cf11f7bf8600e8d0d7d43abb0e11c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239943"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控制項：屬性頁

屬性頁可讓使用者檢視和變更 ActiveX 控制項屬性的 ActiveX 控制項。 藉由叫用控制項屬性對話方塊，其中包含提供自訂的圖形化介面來檢視及編輯控制項屬性的一或多個屬性頁中存取這些屬性。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

ActiveX 控制項屬性頁會顯示在兩種方式：

- 當控制項的屬性的動詞 (**OLEIVERB_PROPERTIES**) 會叫用，控制項便會開啟強制回應屬性對話方塊，其中包含控制項的屬性頁面。

- 容器可以顯示自己會顯示選取之控制項的屬性頁的非強制回應對話方塊方塊。

屬性 對話方塊中 （如下圖所示） 包含區域來顯示目前的屬性頁面上，索引標籤切換 屬性頁，以及執行常見工作，例如關閉 屬性頁 對話方塊中，按鈕的集合取消任何變更，或立即將變更套用至 ActiveX 控制項。

![Circ3 屬性對話方塊](../mfc/media/vc373i1.gif "Circ3 屬性對話方塊") <br/>
內容 對話方塊

本文章涵蓋使用 ActiveX 控制項中的 屬性頁的相關主題。 它們包括：

- [實作 ActiveX 控制項的預設屬性頁面](#_core_implementing_the_default_property_page)

- [將控制項加入至屬性頁](#_core_adding_controls_to_a_property_page)

- [自訂 DoDataExchange 函式](#_core_customizing_the_dodataexchange_function)

如需有關如何使用 ActiveX 控制項中的 屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：新增另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

如需使用屬性工作表以外的 ActiveX 控制項的 MFC 應用程式中的資訊，請參閱[屬性工作表](../mfc/property-sheets-mfc.md)。

##  <a name="_core_implementing_the_default_property_page"></a> 實作 [預設] 屬性頁

如果您使用 ActiveX 控制項精靈來建立您的控制項專案時，ActiveX 控制項精靈提供的預設屬性頁類別控制項衍生自[COlePropertyPage 類別](../mfc/reference/colepropertypage-class.md)。 一開始，此屬性頁面是空白的但您可以將任何對話方塊控制項或一組控制項新增至它。 由於 ActiveX 控制項精靈會建立只有一個屬性頁類別，根據預設，其他的屬性頁面類別 (也衍生自`COlePropertyPage`) 必須使用 類別檢視中建立。 如需有關此程序的詳細資訊，請參閱[MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。

實作的屬性頁面 （在此情況下，預設值） 是一個三步驟程序：

#### <a name="to-implement-a-property-page"></a>若要實作的屬性頁

1. 新增`COlePropertyPage`-衍生的控制項專案的類別。 如果已建立專案，使用 ActiveX 控制項精靈 （在此情況下中），預設屬性頁類別已經存在。

1. 使用對話方塊編輯器，將任何控制項加入至屬性頁範本。

1. 來自訂`DoDataExchange`函式的`COlePropertyPage`-衍生的類別來交換屬性頁控制項和 ActiveX 控制項之間的值。

例如下列程序的目的，使用簡單的控制項 （名為 「 範例 」）。 範例使用 ActiveX 控制項精靈所建立，並包含內建 Caption 屬性。

##  <a name="_core_adding_controls_to_a_property_page"></a> 將控制項加入至屬性頁

#### <a name="to-add-controls-to-a-property-page"></a>將控制項加入至屬性頁

1. 您開啟的控制專案，開啟 [資源檢視]。

1. 按兩下** 對話方塊**directory 圖示。

1. 開啟 [IDD_PROPPAGE_SAMPLE] 對話方塊。

   ActiveX 控制項精靈將專案的名稱附加至對話方塊 ID，在此情況下，範例的結尾。

1. 拖放選取的控制項從工具箱拖曳對話方塊區域。

1. 此範例中，針對文字標籤控制項 」 標題: 「 和編輯方塊控制項 IDC_CAPTION 識別碼就已足夠。

1. 按一下 **儲存**工具列，以儲存您的變更。

既然已修改的使用者介面，您需要連結編輯方塊與 [標題] 屬性。 這是下一節中藉由編輯`CSamplePropPage::DoDataExchange`函式。

##  <a name="_core_customizing_the_dodataexchange_function"></a> 自訂 DoDataExchange 函式

屬性頁[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)函式可讓您連結的內容控制項中的實際值屬性值。 若要建立連結，您必須對應適當的屬性頁面欄位至其個別的控制項屬性。

這些對應會實作使用屬性頁**DDP_** 函式。 **DDP_** 函數的運作類似**DDX_** 使用標準 MFC 對話方塊中，有一個例外狀況的函式。 參考成員變數，除了**DDP_** 函式會採用控制項屬性的名稱。 以下是中的一般項目`DoDataExchange`屬性頁的函式。

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函式產生關聯的屬性頁*m_caption*標題，成員變數使用`DDP_TEXT`函式。

插入屬性頁控制項之後，您需要建立屬性頁控制項、 IDC_CAPTION，與實際的控制項屬性之間的連結標題使用`DDP_Text`函式，如上面所述。

[屬性頁](../mfc/reference/property-pages-mfc.md)可供其他對話方塊控制項類型，例如核取方塊、 選項按鈕和清單方塊。 下表列出的整組屬性頁**DDP_** 函式和其用途：

### <a name="property-page-functions"></a>屬性頁面函式

|函式名稱|使用此函式連結|
|-------------------|-------------------------------|
|`DDP_CBIndex`|與控制項屬性的下拉式方塊中選取的字串索引。|
|`DDP_CBString`|與控制項屬性的下拉式方塊中選取的字串。 所選的字串可以開始使用的相同字母做為屬性的值，但需要完全符合它。|
|`DDP_CBStringExact`|與控制項屬性的下拉式方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|
|`DDP_Check`|與控制項屬性的核取方塊。|
|`DDP_LBIndex`|與控制項屬性的清單方塊中選取的字串索引。|
|`DDP_LBString`|與控制項屬性的清單方塊中選取的字串。 所選的字串可以開始使用的相同字母做為屬性的值，但需要完全符合它。|
|`DDP_LBStringExact`|與控制項屬性的清單方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|
|`DDP_Radio`|與控制項屬性的選項按鈕。|
|`DDP_Text`|與控制項屬性的文字。|

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage 類別](../mfc/reference/colepropertypage-class.md)

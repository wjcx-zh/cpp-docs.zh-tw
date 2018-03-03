---
title: "MFC ActiveX 控制項： 屬性頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dde35df301c34a6c3a29c48d5ad145681b64a72e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控制項：屬性頁
屬性頁面可讓 ActiveX 控制項使用者檢視和變更 ActiveX 控制項的屬性。 藉由叫用控制項屬性對話方塊，其中包含提供自訂的圖形化介面來檢視及編輯控制項屬性的一或多個屬性頁中存取這些屬性。  
  
 ActiveX 控制項屬性頁會顯示兩種方式：  
  
-   當控制項的屬性的動詞 (**OLEIVERB_PROPERTIES**) 會叫用，控制項就會開啟強制回應屬性對話方塊，其中包含控制項的屬性頁面。  
  
-   容器可顯示所選控制項的屬性頁面會顯示其本身非強制回應對話方塊。  
  
 [屬性] 對話方塊 （如下圖所示） 所組成的區域顯示目前的屬性頁上，屬性頁，以及執行常見工作，例如關閉屬性頁對話方塊中，按鈕的集合之間切換索引標籤取消任何變更，或立即將變更套用至 ActiveX 控制項。  
  
 ![Circ3 的屬性的 [內容] 對話方塊](../mfc/media/vc373i1.gif "vc373i1")  
屬性對話方塊  
  
 本文涵蓋的 ActiveX 控制項中使用屬性頁的相關主題。 它們包括：  
  
-   [實作 ActiveX 控制項的預設屬性頁面](#_core_implementing_the_default_property_page)  
  
-   [將控制項加入至屬性頁](#_core_adding_controls_to_a_property_page)  
  
-   [自訂 DoDataExchange 函式](#_core_customizing_the_dodataexchange_function)  
  
 如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：  
  
-   [MFC ActiveX 控制項：新增另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 在 MFC 應用程式以外的 ActiveX 控制項中使用屬性工作表的資訊，請參閱[屬性工作表](../mfc/property-sheets-mfc.md)。  
  
##  <a name="_core_implementing_the_default_property_page"></a>實作預設屬性頁  
 如果您使用 ActiveX 控制項精靈來建立控制項專案時，ActiveX 控制項精靈提供的預設屬性頁類別控制項衍生自[COlePropertyPage 類別](../mfc/reference/colepropertypage-class.md)。 一開始，此屬性頁面是空白的但您可以將任何對話方塊控制項或一組控制項加入它。 因為 ActiveX 控制項精靈會根據預設，其他的屬性頁類別只能有一個屬性頁類別 (也要衍生自`COlePropertyPage`) 必須使用 類別檢視中建立。 如需有關這個程序的詳細資訊，請參閱[MFC ActiveX 控制項： 加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。  
  
 實作屬性頁面 （在此情況下，預設值） 是三個步驟的程序：  
  
#### <a name="to-implement-a-property-page"></a>若要實作的屬性頁  
  
1.  新增`COlePropertyPage`-衍生控制項專案的類別。 如果使用 （如同在此情況下） 的 ActiveX 控制項精靈建立專案，預設屬性頁類別已經存在。  
  
2.  您可以使用對話方塊編輯器來將任何控制項加入屬性頁範本。  
  
3.  自訂`DoDataExchange`函式的`COlePropertyPage`-衍生的類別來交換屬性頁控制項和 ActiveX 控制項之間的值。  
  
 比方說用途，下列程序使用的簡單控制項 （名為 「 範例 」）。 範例使用 ActiveX 控制項精靈所建立，並包含內建標題屬性。  
  
##  <a name="_core_adding_controls_to_a_property_page"></a>將控制項加入至屬性頁  
  
#### <a name="to-add-controls-to-a-property-page"></a>將控制項加入至屬性頁  
  
1.  開啟您控制專案，開啟 [資源檢視]。  
  
2.  按兩下**對話方塊**directory 圖示。  
  
3.  開啟**IDD_PROPPAGE_SAMPLE**  對話方塊。  
  
     ActiveX 控制項精靈會將專案名稱附加至結尾的對話方塊 ID，在此情況下，範例。  
  
4.  拖放選取的控制項從工具箱拖曳至對話方塊中的區域。  
  
5.  例如，文字標籤控制項 」 標題:"和編輯方塊控制項**IDC_CAPTION**識別碼就已足夠。  
  
6.  按一下**儲存**儲存變更 工具列上。  
  
 既然已修改的使用者介面，您需要連結編輯方塊與 [標題] 屬性。 這是下一節中藉由編輯`CSamplePropPage::DoDataExchange`函式。  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a>自訂 DoDataExchange 函式  
 屬性頁[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)函數可讓您將使用內容控制項中的實際值的屬性頁面值連結。 若要建立連結，您必須對應到其各自的控制項屬性的適當的屬性頁面欄位。  
  
 這些對應會實作使用屬性頁**DDP_**函式。 **DDP_**函式**DDX_**標準 MFC 對話方塊中，有一個例外狀況中使用的函數。 參考成員變數，除了**DDP_**函式接受控制項屬性的名稱。 以下是中的一般項目`DoDataExchange`屬性頁的函式。  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 此函式產生關聯的屬性頁的`m_caption`成員變數，其標題中，使用`DDP_TEXT`函式。  
  
 插入屬性頁控制項之後，您需要建立屬性頁控制項之間的連結`IDC_CAPTION`，實際的控制項屬性，標題、 使用和**DDP_Text**函式 （如上所述）。  
  
 [屬性頁](../mfc/reference/property-pages-mfc.md)不適用於其他對話方塊控制項類型，例如核取方塊，選項按鈕和清單方塊。 下表列出屬性頁的整組**DDP_**函式和其用途：  
  
### <a name="property-page-functions"></a>屬性頁函式  
  
|函式名稱|使用此函式連結|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|與控制項屬性的下拉式方塊中選取的字串索引。|  
|`DDP_CBString`|與控制項屬性的下拉式方塊中選取的字串。 選取的字串可以具有相同屬性的值為字母開頭，但需要不一定要完全符合。|  
|`DDP_CBStringExact`|與控制項屬性的下拉式方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|`DDP_Check`|與控制項屬性的核取方塊。|  
|`DDP_LBIndex`|與控制項屬性的清單方塊中選取的字串索引。|  
|`DDP_LBString`|與控制項屬性的清單方塊中選取的字串。 選取的字串可以具有相同屬性的值為字母開頭，但需要不一定要完全符合。|  
|`DDP_LBStringExact`|與控制項屬性的清單方塊中選取的字串。 選取的字串和屬性的字串值必須完全相符。|  
|`DDP_Radio`|與控制項屬性的選項按鈕。|  
|**DDP_Text**|與控制項屬性的文字。|  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage 類別](../mfc/reference/colepropertypage-class.md)

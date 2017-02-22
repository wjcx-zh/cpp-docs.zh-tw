---
title: "MFC ActiveX 控制項：屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPageDialog 類別"
  - "DDP_ 函式"
  - "DoDataExchange 方法"
  - "MFC ActiveX 控制項, 屬性"
  - "MFC ActiveX 控制項, 屬性頁"
  - "OLEIVERB_PROPERTIES"
  - "屬性頁, MFC ActiveX 控制項"
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控制項：屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性頁允許 ActiveX 控制項的使用者檢視和變更 ActiveX 控制項的屬性。  這些屬性以叫用控制項屬性對話方塊來存取，這個對話方塊包含一張以上的屬性頁，提供檢視和編輯控制項屬性要使用的自訂圖形介面。  
  
 ActiveX 控制項屬性頁顯示使用兩種方法:  
  
-   當控制項的屬性動詞命令 \(**OLEIVERB\_PROPERTIES**\) 時叫用，控制開啟包含控制項的屬性頁中 Modal 屬性對話方塊。  
  
-   容器可以顯示選取之控制項的屬性頁的非強制回應對話方塊。  
  
 屬性對話方塊 \(說明在下圖\) 中顯示的目前屬性頁、選項交換在屬性頁之間執行一般工作，例如關閉屬性頁對話方塊，取消任何變更或立即套用至 ActiveX 控制項的按鈕的集合本機變更。  
  
 ![Circ3 的屬性對話方塊](../mfc/media/vc373i1.png "vc373I1")  
屬性對話方塊  
  
 本文包含主題與使用屬性頁與 ActiveX 控制項。  這些需求包括：  
  
-   [實作 ActiveX 控制項的預設屬性頁](#_core_implementing_the_default_property_page)  
  
-   [將控制項加入至屬性工作頁](#_core_adding_controls_to_a_property_page)  
  
-   [自訂 DoDataExchange 函式](#_core_customizing_the_dodataexchange_function)  
  
 如需使用屬性頁的詳細資訊在 ActiveX 控制項，請參閱下列文件:  
  
-   [MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 如需使用屬性工作表的資訊在刪除 ActiveX 控制項之外的 MFC 應用程式，請參閱 [屬性工作表](../mfc/property-sheets-mfc.md)。  
  
##  <a name="_core_implementing_the_default_property_page"></a> 實作預設屬性頁  
 如果您使用 ActiveX 控制項精靈來建立您的控制項專案， ActiveX 控制項精靈可從 [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md)衍生的控制項提供預設屬性頁類別。  最初，這個屬性頁是空白的，不過，您可以加入任何對話方塊控制項或一組控制項。  預設會因為 ActiveX 控制項精靈只建立屬性頁類別，使用類別檢視中，必須建立其他屬性頁類別 \(也是衍生自 `COlePropertyPage`\)。  如需這項程序的詳細資訊，請參閱 [MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。  
  
 實作屬性頁 \(在這種情況下，預設\) 是一個步驟:  
  
#### 實作屬性頁  
  
1.  將`COlePropertyPage`衍生類別加入至 Web 控制項專案。  如果專案建立使用 ActiveX 控制項精靈 \(在此例中\)，預設屬性頁類別已經存在。  
  
2.  使用對話方塊編輯器加入所有控制項屬性頁範本。  
  
3.  自訂 `COlePropertyPage`的 `DoDataExchange` 函式要交換值的衍生類別在屬性頁控制項和 ActiveX 控制項範圍。  
  
 提供示範之用，下列程序使用簡單的控制項 \(名稱為「Sample」\)。  範例會使用 ActiveX 控制項精靈和只包含內建標頭屬性。  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> 將控制項加入至屬性工作頁  
  
#### 將控制項加入至屬性頁  
  
1.  在您的專案中，開啟資源檢視。  
  
2.  按兩下 **Dialog** 目錄圖示。  
  
3.  開啟 **IDD\_PROPPAGE\_SAMPLE** 對話方塊。  
  
     ActiveX 控制項精靈附加專案名稱對話方塊 ID 的結尾，在這種情況下，看範例。  
  
4.  拖放從工具箱中選取的控制項在對話方塊區域上。  
  
5.  在這個範例中，文字標籤控制「標題: 」並與 **IDC\_CAPTION** 識別項的編輯方塊控制項即可。  
  
6.  在工具列上按一下 \[**儲存**\] 以儲存變更。  
  
 現在已修改使用者介面，您需要與標頭屬性連接編輯方塊。  這在下列章節透過編輯 `CSamplePropPage::DoDataExchange` 函式完成。  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> 自訂 DoDataExchange 函式  
 您的屬性頁 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) 函式可讓您使用屬性的實際值在控制項的連接屬性頁值。  若要建立連結，您必須將適當的屬性頁欄位到其各自的控制項屬性。  
  
 使用屬性頁 **DDP\_** 函式實作這些對應。  **DDP\_** 函式的運作方式與在標準 MFC 對話方塊的 **DDX\_** 函式，有一個例外狀況。  除了對成員變數的參考以外， **DDP\_** 函式採用控制項屬性的名稱。  下列是在 `DoDataExchange` 函式中的一般項目屬性頁。  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/CPP/mfc-activex-controls-property-pages_1.cpp)]  
  
 使用 `DDP_TEXT` 函式，此函式相關聯之屬性頁的 `m_caption` 成員變數與標頭。  
  
 將屬性頁控制外掛程式之後，您需要建立上述屬性頁控制項、`IDC_CAPTION`和實際控制項屬性，標頭之間的連結，透過使用 **DDP\_Text** 函式。  
  
 [屬性頁](../mfc/reference/property-pages-mfc.md) 為其他對話方塊控制項類型，例如核取方塊、選項按鈕和清單方塊。  下表列出整組屬性頁 **DDP\_** 函式及其用途:  
  
### 屬性頁函式  
  
|函式名稱|使用這個函式連接|  
|----------|--------------|  
|`DDP_CBIndex`|在下拉式方塊中選取有控制項屬性的索引的字串。|  
|`DDP_CBString`|在下拉式方塊中選取有控制項屬性的字串。  選取的字串可能以字母開頭和屬性值相同，但不需要完全相符。|  
|`DDP_CBStringExact`|在下拉式方塊中選取有控制項屬性的字串。  選取的資料和屬性的字串值必須完全相符。|  
|`DDP_Check`|控制項有屬性的核取方塊。|  
|`DDP_LBIndex`|在清單方塊中選取有控制項屬性的索引的字串。|  
|`DDP_LBString`|在清單方塊中選取有控制項屬性的字串。  選取的字串可能以字母開頭和屬性值相同，但不需要完全相符。|  
|`DDP_LBStringExact`|在清單方塊中選取有控制項屬性的字串。  選取的資料和屬性的字串值必須完全相符。|  
|`DDP_Radio`|控制項有屬性的一個選項按鈕。|  
|**DDP\_Text**|控制項屬性中的文字。|  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md)
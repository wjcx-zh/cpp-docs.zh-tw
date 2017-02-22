---
title: "MFC ActiveX 控制項：加入內建屬性 | Microsoft Docs"
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
  - "BackColor 屬性"
  - "ForeColor 屬性"
  - "前景色彩"
  - "前景色彩, ActiveX 控制項"
  - "MFC ActiveX 控制項, 屬性"
  - "屬性 [MFC], 加入內建"
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控制項：加入內建屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內建屬性與自訂屬性不同它們的類別 `COleControl`已經實作。  `COleControl` 包含預先定義的成員函式控制項支援通用屬性。  一些通用屬性包含控制項的標題和前景和背景色彩。  如需其他內建屬性的詳細資訊，請參閱本主題稍後的 [加入屬性精靈支援的內建屬性。](#_core_stock_properties_supported_by_classwizard) 文章。  內建屬性的分派對應項目由 **DISP\_STOCKPROP**一律加上前置字元。  
  
 本文說明如何將內建屬性 \(在這種情況下，標題\) 加入至 ActiveX 控制項加入屬性精靈並說明產生的程式碼修改。  主題包括：  
  
-   [使用將加入屬性精靈的內建屬性。](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [加入屬性內建屬性的精靈變更](#_core_classwizard_changes_for_stock_properties)  
  
-   [加入屬性精靈支援的內建屬性。](#_core_stock_properties_supported_by_classwizard)  
  
-   [內建屬性和告知](#_core_stock_properties_and_notification)  
  
-   [色彩屬性](#_core_color_properties)  
  
    > [!NOTE]
    >  Visual Basic 自訂控制項通常會有屬性，例如 Top，寬度、高度、對齊、標記、名稱、TabIndex、TabStop 和父代。  ActiveX 控制項容器，然而，對實作這些控制項屬性負責同時 ActiveX 控制項不應支援這些屬性。  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> 使用將加入屬性精靈的內建屬性。  
 因為支援屬性由 `COleControl`，自動將內建屬性來將自訂屬性需要較少的程式碼。  下列程序示範將內建標頭屬性加入至 ActiveX 控制項架構，而且也可以加入其他內建屬性。  用標題替代選擇的內建屬性名稱。  
  
#### 使用加入屬性精靈，將內建的標題屬性  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表中，按一下 \[加入\]，再按一下 \[**加入屬性**\]。  
  
     這樣會開啟 [加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在 **Property Name** 方塊中，按一下 **Caption**。  
  
6.  按一下 \[**完成**\]。  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> 加入屬性內建屬性的精靈變更  
 由於 `COleControl` 支援內建屬性，加入屬性精靈在任何情況下都不會變更類別宣告;它將屬性加入至分派對應。  加入屬性精靈會將下列行加入至控制項的分派對應，位於實作 \(.CPP\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 下列程式碼行加入至控制項的介面描述 \(.IDL\) 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 此行指派標題屬性特定 ID.  請注意屬性為可繫結，並在修改值之前要求資料庫的使用權限。  
  
 這個標頭屬性提供給控制項的使用者。  若要使用內建屬性的值，請存取 `COleControl` 基底類別的成員變數或成員函式。  如需這些成員變數和成員函式的詳細資訊，請參閱下一節，加入屬性精靈支援的內建屬性。  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> 加入屬性精靈支援的內建屬性。  
 `COleControl` 類別提供九個內建屬性。  您可以將使用加入屬性精靈，您要的屬性。  
  
|屬性|分派對應項目|如何存取值。|  
|--------|------------|------------|  
|**外觀**|**DISP\_STOCKPROP\_APPEARANCE \(\)**|做為 **m\_sAppearance**的值可存取的。|  
|`BackColor`|**DISP\_STOCKPROP\_BACKCOLOR \(\)**|值可以藉由呼叫 `GetBackColor`。|  
|`BorderStyle`|**DISP\_STOCKPROP\_BORDERSTYLE \(\)**|做為 **m\_sBorderStyle**的值可存取的。|  
|**Caption**|**DISP\_STOCKPROP\_CAPTION \(\)**|值可以藉由呼叫 `InternalGetText`。|  
|**已啟用**|**DISP\_STOCKPROP\_ENABLED \(\)**|做為 **m\_bEnabled**的值可存取的。|  
|**Font**|**DISP\_STOCKPROP\_FONT \(\)**|使用方式參閱本文 [MFC ActiveX 控制項:使用字型](../mfc/mfc-activex-controls-using-fonts.md) 。|  
|`ForeColor`|**DISP\_STOCKPROP\_FORECOLOR \(\)**|值可以藉由呼叫 `GetForeColor`。|  
|**hWnd**|**DISP\_STOCKPROP\_HWND\( \)**|值可以為 `m_hWnd`。|  
|**文字**|**DISP\_STOCKPROP\_TEXT\( \)**|值可以藉由呼叫 `InternalGetText`。  這個屬性會與 **Caption**，除了屬性名稱。|  
|**ReadyState**|**DISP\_STOCKPROP\_READYSTATE \(\)**|做為 m\_lReadyState 或 `GetReadyState`的值可供存取|  
  
##  <a name="_core_stock_properties_and_notification"></a> 內建屬性和告知  
 大部分的內建屬性具有可覆寫的告知功能。  例如，在中，當 `BackColor` 屬性變更時， `OnBackColorChanged` 函式 \(控制項類別的成員函式\) 呼叫。  預設實作\(在`COleControl`中\)會呼叫 `InvalidateControl`。  覆寫這個函式要採取其他動作以回應這個情況。  
  
##  <a name="_core_color_properties"></a> 色彩屬性  
 則繪製控制項時，您可以使用內建 `ForeColor` 和 `BackColor` 屬性，或者您的自訂色彩屬性。  若要使用色彩屬性，請呼叫 [COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md) 成員函式。  這個函式參數是色彩屬性的值和選擇性調色盤控制代碼。  傳回值是可傳遞至 GDI 函式，例如 `SetTextColor` 和 `CreateSolidBrush`的 **COLORREF** 值。  
  
 內建 `ForeColor` 和 `BackColor` 屬性的色彩值是透過呼叫 `GetForeColor` 或 `GetBackColor` 函式存取，分別。  
  
 則繪製控制項時，下列範例將示範如何使用這兩個色彩屬性。  它使用暫存 **COLORREF** 變數和 `CBrush` 物件與呼叫 `TranslateColor`:使用 `ForeColor` 屬性和其他使用 `BackColor` 屬性。  暫存 `CBrush` 物件會用來繪製控制項的矩形，請使用 `ForeColor` 屬性，因此，文字色彩設定。  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)
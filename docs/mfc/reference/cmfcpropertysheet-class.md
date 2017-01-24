---
title: "CMFCPropertySheet Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertySheet class"
  - "CMFCPropertySheet::OnInitDialog method"
  - "CMFCPropertySheet::PreTranslateMessage method"
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertySheet` 類別支援屬性工作表，其中每個屬性頁是由頁面索引標籤、工具列按鈕、樹狀目錄控制項節點或清單項目所表示。  
  
## 語法  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertySheet::CMFCPropertySheet](../Topic/CMFCPropertySheet::CMFCPropertySheet.md)|建構 `CMFCPropertySheet` 物件。|  
|`CMFCPropertySheet::~CMFCPropertySheet`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md)|將頁面新增至屬性工作表。|  
|[CMFCPropertySheet::AddPageToTree](../Topic/CMFCPropertySheet::AddPageToTree.md)|將新的屬性頁新增至樹狀目錄控制項。|  
|[CMFCPropertySheet::AddTreeCategory](../Topic/CMFCPropertySheet::AddTreeCategory.md)|將新的節點新增至樹狀目錄控制項。|  
|[CMFCPropertySheet::EnablePageHeader](../Topic/CMFCPropertySheet::EnablePageHeader.md)|在每個頁面頂端保留空間以繪製自訂標頭。|  
|[CMFCPropertySheet::GetHeaderHeight](../Topic/CMFCPropertySheet::GetHeaderHeight.md)|擷取目前標頭的高度。|  
|[CMFCPropertySheet::GetLook](../Topic/CMFCPropertySheet::GetLook.md)|擷取指定目前屬性工作表外觀的列舉值。|  
|[CMFCPropertySheet::GetNavBarWidth](../Topic/CMFCPropertySheet::GetNavBarWidth.md)|重試巡覽列的寬度，以像素為單位。|  
|[CMFCPropertySheet::GetTab](../Topic/CMFCPropertySheet::GetTab.md)|擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。|  
|`CMFCPropertySheet::GetThisClass`|由取得與此類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件標的架構使用。|  
|[CMFCPropertySheet::InitNavigationControl](../Topic/CMFCPropertySheet::InitNavigationControl.md)|初始化目前屬性工作表控制項的外觀。|  
|[CMFCPropertySheet::OnActivatePage](../Topic/CMFCPropertySheet::OnActivatePage.md)|啟用屬性頁時由架構呼叫。|  
|[CMFCPropertySheet::OnDrawPageHeader](../Topic/CMFCPropertySheet::OnDrawPageHeader.md)|由架構呼叫以繪製自訂屬性頁標頭。|  
|`CMFCPropertySheet::OnInitDialog`|處理 [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) 訊息。  \(覆寫 [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)。\)|  
|[CMFCPropertySheet::OnRemoveTreePage](../Topic/CMFCPropertySheet::OnRemoveTreePage.md)|由架構呼叫以從樹狀目錄控制項移除屬性頁。|  
|`CMFCPropertySheet::PreTranslateMessage`|轉譯分派至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前的視窗訊息。  \(覆寫 `CPropertySheet::PreTranslateMessage`。\)|  
|[CMFCPropertySheet::RemoveCategory](../Topic/CMFCPropertySheet::RemoveCategory.md)|從樹狀目錄控制項移除節點。|  
|[CMFCPropertySheet::RemovePage](../Topic/CMFCPropertySheet::RemovePage.md)|從屬性工作表中移除屬性頁。|  
|[CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md)|指定在 Outlook 窗格之導覽控制項中使用的映像清單。|  
|[CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md)|指定屬性工作表的外觀。|  
  
## 備註  
 `CMFCPropertySheet` 類別表示屬性工作表，也稱為索引標籤對話方塊。  `CMFCPropertySheet` 類別能以各種方式顯示屬性頁。  
  
 請執行下列步驟，在應用程式中使用 `CMFCPropertySheet` 類別。  
  
1.  自 `CMFCPropertySheet` 類別衍生類別並加以命名，例如，CMyPropertySheet。  
  
2.  為每個屬性頁建構 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) 物件。  
  
3.  在 CMyPropertySheet 建構函式中呼叫 [CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md) 方法。  該方法的參數會指定屬性頁應該要顯示為沿著屬性工作表頂端或左邊的索引標籤；Microsoft OneNote 屬性工作表樣式的索引標籤；在 Microsoft Outlook 工具列控制項上的按鈕；在樹狀目錄控制項上的節點；或在屬性工作表左邊的項目清單。  
  
4.  如果您以 Microsoft Outlook 工具列的樣式建立屬性工作表，請呼叫 [CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md) 方法，以建立映像清單與屬性頁之間的關聯。  
  
5.  為每個屬性頁呼叫 [CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md) 方法。  
  
6.  建立 `CMFCPropertySheet` 控制項，並呼叫其 `DoModal` 方法。  
  
## 插圖  
 下圖描述其樣式為內嵌 Microsoft Outlook 工具列的屬性工作表。  Outlook 工具列會出現在屬性工作表的左邊。  
  
 ![CMFCPropertySheet 色彩控制項](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet\_color")  
  
 下圖描述包含 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) 物件的屬性工作表。  該物件是樣式為標準通用控制項屬性頁的屬性工作表。  
  
 ![CMFCPropertySheet 清單和屬性控制項](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet\_list")  
  
 下圖描述其樣式為樹狀目錄控制項的屬性工作表。  
  
 ![屬性樹狀目錄](../Image/PropTree.png "PropTree")  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## 需求  
 **標頭：**afxpropertysheet.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage Class](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
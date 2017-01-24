---
title: "CMFCToolBarsCustomizeDialog Class | Microsoft Docs"
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
  - "CMFCToolBarsCustomizeDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarsCustomizeDialog class"
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarsCustomizeDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓使用者自訂工具列、功能表、鍵盤快速鍵、使用者定義的工具和視覺化樣式在應用程式中的非強制回應對話方塊的索引標籤對話方塊 \([CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)\)。  通常，使用者存取這個對話方塊來選取 \[**自訂**\] 從 \[**工具**\] 功能表。  
  
 \[**自訂**\] 對話方塊有六個索引標籤: \[**命令**\]\[**工具列**\]\[**工具**\]、、、、和 \[**鍵盤**\]\[**功能表**\]\[**選項**\]。  
  
## 語法  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](../Topic/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog.md)|建構 `CMFCToolBarsCustomizeDialog` 物件。|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md)|插入工具列按鈕會在 \[**命令**\] 網頁的命令清單。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](../Topic/CMFCToolBarsCustomizeDialog::AddMenu.md)|從資源檔載入功能表並呼叫 [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) 加入該功能表加入 \[**命令**\] 網頁的命令清單。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md)|從資源檔載入功能表並呼叫 [CMFCToolBarsCustomizeDialog::AddMenuCommands](../Topic/CMFCToolBarsCustomizeDialog::AddMenuCommands.md) 加入該功能表加入 \[**命令**\] 網頁的命令清單。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](../Topic/CMFCToolBarsCustomizeDialog::AddToolBar.md)|從資源檔載入一個工具列。  然後，，才能在  功能表上的每個命令在 \[**命令**\] 網頁的命令清單中呼叫方法 [CMFCToolBarsCustomizeDialog::AddButton](../Topic/CMFCToolBarsCustomizeDialog::AddButton.md) 插入按鈕可在指定分類中。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md)|顯示 \[**自訂**\] 對話方塊。|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](../Topic/CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars.md)|您可以使用 \[**自訂**\] 對話方塊，以啟用或停用建立新的工具列。|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](../Topic/CMFCToolBarsCustomizeDialog::FillAllCommandsList.md)|填入的命令所提供的 `CListBox` 物件在 \[**所有命令**\] 分類。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox.md)|填入每個命令分類名稱提供的 `CComboBox` 物件在 \[**自訂**\] 對話方塊的 。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](../Topic/CMFCToolBarsCustomizeDialog::FillCategoriesListBox.md)|填入每個命令分類名稱提供的 `CListBox` 物件在 \[**自訂**\] 對話方塊的 。|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](../Topic/CMFCToolBarsCustomizeDialog::GetCommandName.md)|擷取與指定命令 ID. 的名稱|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](../Topic/CMFCToolBarsCustomizeDialog::GetCountInCategory.md)|擷取具有指定之文字標籤項目數目所提供清單中的。|  
|[CMFCToolBarsCustomizeDialog::GetFlags](../Topic/CMFCToolBarsCustomizeDialog::GetFlags.md)|擷取影響對話方塊之行為的旗標集。|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](../Topic/CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage.md)|開始使用影像編輯器，讓使用者可以自訂工具列按鈕或功能表項目圖示。|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](../Topic/CMFCToolBarsCustomizeDialog::OnInitDialog.md)|覆寫擴大屬性工作表初始化。  \(覆寫 [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)\)。|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](../Topic/CMFCToolBarsCustomizeDialog::PostNcDestroy.md)|呼叫框架，以在終結後視窗。  \(覆寫 `CPropertySheet::PostNcDestroy`\)。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](../Topic/CMFCToolBarsCustomizeDialog::RemoveButton.md)|移除按鈕具有指定的命令 ID 從指定的類別，或從所有分類。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](../Topic/CMFCToolBarsCustomizeDialog::RenameCategory.md)|在清單方塊中的分類來取代 \[**命令**\] 索引標籤的分類。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md)|以新的工具列按鈕物件取代在 \[**命令**\] 選項的命令清單中的  按鈕。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](../Topic/CMFCToolBarsCustomizeDialog::SetUserCategory.md)|將類別加入至 \[**命令**\] 索引標籤會顯示分類清單。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](../Topic/CMFCToolBarsCustomizeDialog::CheckToolsValidity.md)|呼叫由架構判斷使用者定義的工具清單是否有效。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnAfterChangeTool.md)|呼叫框架，以使用者定義的工具變更的屬性。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](../Topic/CMFCToolBarsCustomizeDialog::OnAssignKey.md)|判斷指定的鍵盤快速鍵是否能為動作。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](../Topic/CMFCToolBarsCustomizeDialog::OnBeforeChangeTool.md)|判斷是否可以變更其中一個使用者定義的工具。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](../Topic/CMFCToolBarsCustomizeDialog::OnInitToolsPage.md)|呼叫，便會由架構使用者選取時 \[**工具**\] 選項需要。|  
  
## 備註  
 若要顯示 \[**自訂**\] 對話方塊，請建立 `CMFCToolBarsCustomizeDialog` 物件並呼叫 [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md) 方法。  
  
 當 \[**自訂**\] 對話方塊在作用中時，應用程式會限制使用者自訂工作的特殊模式下運作。  
  
## 範例  
 下列範例會在 `CMFCToolBarsCustomizeDialog` 類別會示範如何使用各種方法。  您可以使用 \[**自訂**\] 對話方塊，這個範例示範如何取代在清單方塊中的工具列按鈕。 \[**命令**\] 網頁的命令，以建立新的工具列和顯示 \[**自訂**\] 對話方塊。  這個程式碼片段是 [IE 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/CPP/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)  
  
## 需求  
 **標題:** afxToolBarsCustomizeDialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)
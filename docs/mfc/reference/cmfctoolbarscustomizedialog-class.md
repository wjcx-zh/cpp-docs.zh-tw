---
title: CMFCToolBarsCustomizeDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b4c2d7de8c9be8aa33cd5849c089a2caac1271b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041873"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 類別
非強制回應索引標籤對話方塊 ( [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md))，可讓使用者自訂工具列、 功能表、 鍵盤快速鍵、 使用者定義的工具和應用程式中的視覺化樣式。 使用者通常會選取 [ **工具** ] 功能表中的 [ **自訂** ]，以存取這個對話方塊。  
  
 **自訂**對話方塊有六個索引標籤：**命令**，**工具列**，**工具**，**鍵盤**， **功能表**，和**選項**。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|建構 `CMFCToolBarsCustomizeDialog` 物件。|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|插入命令的清單中的工具列按鈕，在**命令**頁面|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|載入功能表資源並呼叫從[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)加入該功能表命令的清單上**命令**頁面。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|載入功能表資源並呼叫從[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)加入該功能表命令的清單上**命令**頁面。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|從資源載入工具列。 然後，針對每個命令的功能表呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法插入的命令清單中的按鈕上**命令**指定類別下的頁面。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|顯示**自訂** 對話方塊。|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|啟用或停用使用建立新的工具列**自訂** 對話方塊。|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|填入提供`CListBox`物件中的命令與**所有命令**類別目錄。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|填入提供`CComboBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|填入提供`CListBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|擷取與指定的命令識別碼相關聯的名稱|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|擷取具有指定的文字標籤中提供的清單項目數目。|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|擷取影響行為的對話方塊中的旗標組。|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|啟動影像編輯器，以便讓使用者可自訂工具列按鈕或功能表項目圖示。|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|覆寫以擴大屬性工作表的初始設定。 (覆寫[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|終結視窗後，由架構呼叫。 (覆寫 `CPropertySheet::PostNcDestroy`。)|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|從指定的類別，或從所有類別目錄中移除具有指定的命令 ID 的按鈕。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|在重新命名類別的清單方塊中的類別**命令** 索引標籤。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|取代命令的清單中的按鈕上**命令** 索引標籤，以新的工具列按鈕物件。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|將分類加入至類別，將會顯示在清單**命令** 索引標籤。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|由架構呼叫以判斷是否為有效的使用者定義的工具清單。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|使用者定義的工具的內容變更時由架構呼叫。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|判斷指定的鍵盤快速鍵是否可以指派給動作。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|決定是否可以變更使用者定義的工具。|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|由架構呼叫，當使用者選擇**工具**要求 索引標籤。|  
  
## <a name="remarks"></a>備註  
 若要顯示**自訂**對話方塊方塊中，建立`CMFCToolBarsCustomizeDialog`物件並呼叫[CMFCToolBarsCustomizeDialog::Create](#create)方法。  
  
 雖然**自訂**對話方塊的 作用中時，應用程式限制的自訂工作使用者使用特殊模式運作。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBarsCustomizeDialog`類別。 此範例示範如何在取代工具列按鈕在清單方塊中的命令**命令**頁面上，讓您藉由建立新的工具列**自訂**對話方塊中，並顯示**自訂** 對話方塊。 此程式碼片段是部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>需求  
 **標頭：** afxToolBarsCustomizeDialog.h  
  
##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton  
 插入命令的清單中的工具列按鈕，在**命令**頁面。  
  
```  
void AddButton(
    UINT uiCategoryId,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiCategoryId*  
 指定要插入按鈕的類別識別碼。  
  
 [in]*按鈕*  
 指定要插入的按鈕。  
  
 [in]*iInsertBefore*  
 指定工具列按鈕之前插入按鈕的以零為起始的索引。  
  
 [in]*lpszCategory*  
 指定要插入按鈕的類別目錄字串。  
  
### <a name="remarks"></a>備註  
 `AddButton`方法會忽略有標準命令 Id （例如 ID_FILE_MRU_FILE1) 的按鈕、 不允許的命令 (請參閱[CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虛擬按鈕。  
  
 這個方法會建立新的物件做為相同型別的`button`(通常[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)) 使用按鈕的執行階段類別。 然後它會呼叫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)来複製的資料成員 按鈕，並將複本插入到指定的分類。  
  
 當插入新的按鈕時，它會收到`OnAddToCustomizePage`通知。  
  
 如果`iInsertBefore`為-1，按鈕會附加至類別目錄的清單; 否則它會插入具有指定之索引的項目之前。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`AddButton`方法`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是部分[滑桿範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu  
 載入功能表資源並呼叫從[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)加入該功能表命令的清單上**命令**頁面。  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiMenuResId*  
 指定要載入功能表資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功; 新增功能表否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 在呼叫`AddMenuCommands`， *bPopup*是`FALSE`。 如此一來，該方法不會新增包含的命令清單的子功能表的功能表項目。 這個方法未加入的功能表項目中的子功能表命令的清單。  
  
##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands  
 將項目加入至清單中的命令**命令**頁面以表示指定的功能表中的所有項目。  
  
```  
void AddMenuCommands(
    const CMenu* pMenu,  
    BOOL bPopup,  
    LPCTSTR lpszCategory=NULL,  
    LPCTSTR lpszMenuPath=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*pMenu*  
 要加入的 CMenu 物件指標。  
  
 [in]*bPopup*  
 指定是否要插入的快顯功能表項目清單的命令。  
  
 [in]*lpszCategory*  
 要插入的功能表的類別目錄名稱。  
  
 [in]*lpszMenuPath*  
 命令中顯示時，就會加入至名稱的前置詞**所有類別目錄**清單。  
  
### <a name="remarks"></a>備註  
 `AddMenuCommands`方法迴圈發生於功能表項目所有*pMenu*。 每個功能表項目不包含子功能表，這個方法會建立[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件並呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法將功能表項目新增為工具列按鈕至命令清單**命令**頁面。 分隔符號會忽略在此程序。  
  
 如果*bPopup*是`TRUE`，這個方法會建立每個含有子功能表的功能表項目的[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件，並將它插入命令的清單，藉由呼叫`AddButton`. 否則包含子功能表的功能表項目不會顯示在清單中的命令。 在任一情況下，當`AddMenuCommands`遇到功能表項目具有子功能表它會呼叫本身以遞迴方式，將指標傳遞到做為子功能表*pMenu*參數和附加的子功能表標籤*lpszMenuPath*.  
  
##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar  
 從資源載入工具列。 然後，針對每個命令的功能表呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法插入的命令清單中的按鈕上**命令**指定類別下的頁面。  
  
```  
BOOL AddToolBar(
    UINT uiCategoryId,  
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,  
    UINT uiToolbarResId);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiCategoryId*  
 指定的類別目錄新增工具列資源 ID。  
  
 [in]*uiToolbarResId*  
 指定的資源識別碼的工具列，其命令插入命令的清單。  
  
 [in]*lpszCategory*  
 指定要在其中加入工具列的類別目錄的名稱。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法成功。否則`FALSE`。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`AddToolBar`方法中的`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>備註  
 用來代表每個命令的控制項是[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件。 新增工具列之後，您可以藉由呼叫使用衍生類型的控制項取代按鈕[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)。  
  
##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 驗證的使用者工具清單的有效性。  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>參數  
 [in]*lstTools*  
 使用者定義工具會檢查清單。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`使用者定義的工具清單是否有效，否則`FALSE`。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以確認有效性的物件，代表所傳回的使用者定義工具[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)。  
  
 覆寫`CheckToolsValidity`從衍生類別中的方法`CMFCToolBarsCustomizeDialog`如果您想要驗證的使用者工具之前在使用者關閉對話方塊。 如果此方法傳回`FALSE`當使用者按一下**關閉**右上角的對話方塊或按鈕按鈕**關閉**對話方塊右下角對話方塊會顯示**工具**而不是關閉的索引標籤。 如果此方法傳回`FALSE`當使用者按一下索引標籤以離開的**工具**索引標籤上，瀏覽不會發生。 您應該會顯示適當的訊息方塊，以通知使用者造成驗證失敗的問題。  
  
##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
 建構 `CMFCToolBarsCustomizeDialog` 物件。  
  
```  
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bAutoSetFromMenus = FALSE,  
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),  
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*pWndParentFrame*  
 父框架指標。 此參數不得為 `NULL`。  
  
 [in]*bAutoSetFromMenus*  
 布林值，指定是否要加入功能表命令從所有的功能表命令的清單上**命令**頁面。 如果這個參數是`TRUE`，加入功能表命令。 否則，不會加入功能表命令。  
  
 [in]*uiFlags*  
 影響行為的對話方塊中的旗標的組合。 這個參數可以是一或多個下列值：  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [in]*plistCustomPages*  
 清單的指標`CRuntimeClass`物件，以指定其他的自訂頁面。  
  
### <a name="remarks"></a>備註  
 *PlistCustomPages*參數的清單是指`CRuntimeClass`物件，以指定其他的自訂頁面。 建構函式將更多的頁面加入至對話方塊使用[CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法。 請參閱 CustomPages 範例的範例，加入更多的頁面**自訂** 對話方塊。  
  
 如需詳細資訊，您可以傳入之值的相關*uiFlags*參數，請參閱[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是部分[自訂網頁範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create  
 顯示**自訂** 對話方塊。  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果成功，建立自訂的屬性工作表否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫`Create`只之後您完全初始化類別的方法。  
  
##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 啟用或停用使用建立新的工具列**自訂** 對話方塊。  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bEnable*  
 `TRUE` 若要啟用的使用者定義的工具列。`FALSE`停用工具列。  
  
### <a name="remarks"></a>備註  
 如果*bEnable*是`TRUE`、**新增**，**重新命名**和**刪除**按鈕會顯示在**工具列**頁面。  
  
 根據預設，或者如果*bEnable*是`FALSE`不會顯示這些按鈕，使用者無法定義新的工具列。  
  
##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 填入提供`CListBox`物件中的命令與**所有命令**類別目錄。  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `wndListOfCommands`  
 若要參考`CListBox`來擴展物件。  
  
### <a name="remarks"></a>備註  
 **所有命令**類別所包含的所有類別目錄的命令。 [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法會將命令所提供的按鈕以關聯**所有命令**為您的類別。  
  
 這個方法會清除的內容提供`CListBox`之前填入中的命令物件**所有命令**類別目錄。  
  
 `CMFCMousePropertyPage`類別會使用這個方法來填入按兩下事件清單方塊。  
  
##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
 填入提供`CComboBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。  
  
```  
void FillCategoriesComboBox(
    CComboBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [out]*wndCategory*  
 若要參考`CComboBox`來擴展物件。  
  
 [in]*bAddEmpty*  
 布林值，指定是否要將分類加入至下拉式方塊沒有命令。 如果這個參數是`TRUE`，空的類別目錄會加入至下拉式方塊。 否則，不會加入空的類別。  
  
### <a name="remarks"></a>備註  
 這個方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)方法不同之處在於此方法搭配`CComboBox`物件。  
  
 這個方法不會清除的內容`CComboBox`之前擴展物件。 它可確保**所有命令**類別是下拉式方塊中的最後一個項目。  
  
 您可以藉由加入新的命令類別[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 您可以變更現有的類別目錄的名稱使用[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`類別會使用這個方法來分類鍵盤對應。  
  
##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
 填入提供`CListBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。  
  
```  
void FillCategoriesListBox(
    CListBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [out]*wndCategory*  
 若要參考`CListBox`來擴展物件。  
  
 [in]*bAddEmpty*  
 布林值，指定是否要將類別新增至清單方塊沒有命令。 如果這個參數是`TRUE`，空的類別目錄會加入至清單方塊。 否則，不會加入空的類別。  
  
### <a name="remarks"></a>備註  
 這個方法就像[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)方法不同之處在於此方法搭配`CListBox`物件。  
  
 這個方法不會清除的內容`CListBox`之前擴展物件。 它可確保**所有命令**類別目錄是清單方塊中的最後一個項目。  
  
 您可以藉由加入新的命令類別[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 您可以變更現有的類別目錄的名稱使用[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。  
  
 `CMFCToolBarsCommandsPropertyPage`類別會使用這個方法，以顯示與每個命令類別目錄相關聯的命令清單。  
  
##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName  
 擷取與指定的命令識別碼相關聯的名稱  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*uiCmd*  
 要擷取的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 指定的命令識別碼相關聯的名稱或`NULL`如果命令不存在。  
  
##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory  
 擷取具有指定的文字標籤中提供的清單項目數目。  
  
```  
int GetCountInCategory(
    LPCTSTR lpszItemName,  
    const CObList& lstCommands) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszItemName*  
 要比對的文字標籤。  
  
 [in]*lstCommands*  
 參考清單，其中包含`CMFCToolBarButton`物件。  
  
### <a name="return-value"></a>傳回值  
 所提供的項目數清單的文字標籤等於*lpszItemName*。  
  
### <a name="remarks"></a>備註  
 提供的物件清單中的每個項目必須是型別`CMFCToolBarButton`。 這個方法會比較*lpszItemName*與[CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)資料成員。  
  
##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags  
 擷取影響行為的對話方塊中的旗標組。  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>傳回值  
 影響行為的對話方塊中的旗標組。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取的值*uiFlags*傳遞至建構函式的參數。 傳回值可以是一或多個下列值：  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 可讓使用者指定陰影功能表的外觀。  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 可讓使用者能夠指定是否顯示文字標籤的工具列按鈕影像之下。  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 可讓使用者指定的動畫功能表樣式。  
  
 `AFX_CUSTOMIZE_NOHELP`  
 移除 [自訂] 對話方塊的 [說明] 按鈕。  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 可讓`WS_EX_CONTEXTHELP`視覺化樣式。  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 移除**工具**從自訂對話方塊的頁面。 這個旗標無效，如果您的應用程式使用`CUserToolsManager`類別。  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 可讓按鈕標題包含連字號 ( **&**) 字元。  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 移除**大圖示**從自訂對話方塊中的選項。  
  
 如需有關`WS_EX_CONTEXTHELP`視覺化樣式，請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。  
  
##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 只有在發生後立即回應中的使用者工具的變更。  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>參數  
 [in、 out]*pSelTool*  
 已變更的使用者工具物件的指標。  
  
### <a name="remarks"></a>備註  
 當使用者變更的使用者定義的工具屬性，這個方法是由架構呼叫。 預設實作不做任何動作。 衍生自的類別中置換此方法`CMFCToolBarsCustomizeDialog`執行處理後的使用者工具的變更，就會發生。  
  
##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey  
 驗證使用者定義的鍵盤快速鍵。  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>參數  
 [in、 out]*pAccel*  
 指標會表示為建議的鍵盤指派[快速鍵](http://msdn.microsoft.com/library/windows/desktop/ms646340)結構。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果可以指定索引鍵，或`FALSE`如果不指定索引鍵。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 覆寫此方法，執行額外處理，當使用者指派新的鍵盤快速鍵或鍵盤快速鍵驗證的使用者定義的衍生類別中。 若要防止捷徑指派，傳回`FALSE`。 您應該也會顯示訊息方塊或否則告知使用者為什麼鍵盤快速鍵已被拒絕的原因。  
  
##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 執行自訂處理時的使用者工具變更使用者即將套用變更時。  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>參數  
 [in、 out]*pSelTool*  
 即將被取代的使用者工具物件的指標。  
  
### <a name="remarks"></a>備註  
 使用者定義的工具的內容變更時，這個方法是由架構呼叫。 預設實作不做任何動作。 覆寫`OnBeforeChangeTool`從衍生類別中的方法`CMFCToolBarsCustomizeDialog`如果您想要執行處理序的使用者工具的變更發生，例如釋放資源之前， *pSelTool*使用。  
  
##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
 啟動影像編輯器，以便讓使用者可自訂工具列按鈕或功能表項目圖示。  
  
```  
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,  
    CBitmap& bitmap,  
    int nBitsPerPixel);
```  
  
### <a name="parameters"></a>參數  
 [in]*pWndParent*  
 父視窗的指標。  
  
 [in]*點陣圖*  
 若要編輯點陣圖物件的參考。  
  
 [in]*nBitsPerPixel*  
 點陣圖色彩解析度，以位元 / 像素。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果在認可變更。，否則`FALSE`。 預設實作會顯示一個對話方塊，並傳回`TRUE`如果使用者按一下**確定**，或`FALSE`如果使用者按一下**取消**或**關閉**按鈕。  
  
### <a name="remarks"></a>備註  
 使用者執行影像編輯器時，這個方法是由架構呼叫。 預設實作會顯示[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md) 對話方塊。 覆寫`OnEditToolbarMenuImage`使用自訂影像編輯器的衍生類別中。  
  
##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog  
 覆寫以擴大屬性工作表的初始設定。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 呼叫[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)，藉由顯示**關閉** 按鈕，藉由確認對話方塊中，以符合目前的螢幕大小，以及移動**協助** 對話方塊的左下角的按鈕。  
  
##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 會將架構從通知處理，**工具**頁面即將進行初始化。  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 覆寫這個方法在衍生類別處理此通知中。  
  
##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy  
 終結視窗後，由架構呼叫。  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， `CPropertySheet::PostNcDestroy`，藉由還原為先前模式應用程式。  
  
 [CMFCToolBarsCustomizeDialog::Create](#create)方法會讓應用程式中使用特殊模式，以限制使用者的自訂工作。  
  
##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton  
 從指定的類別，或從所有類別目錄中移除具有指定的命令 ID 的按鈕。  
  
```  
int RemoveButton(
    UINT uiCategoryId,  
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,  
    UINT uiCmdId);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiCategoryId*  
 指定要從中移除按鈕的類別識別碼。  
  
 [in]*uiCmdId*  
 指定按鈕的命令識別碼。  
  
 [in]*lpszCategory*  
 指定要從中移除按鈕的類別目錄的名稱。  
  
### <a name="return-value"></a>傳回值  
 [移除] 按鈕，則為-1 指定的類別目錄中找不到指定的命令 ID 的以零為起始的索引。 如果*uiCategoryId*為-1，傳回值是 0。  
  
### <a name="remarks"></a>備註  
 若要移除所有類別目錄中的按鈕，呼叫這個方法與設定的第一個多載*uiCategoryId*為-1。  
  
##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory  
 在重新命名類別的清單方塊中的類別**命令**頁面。  
  
```  
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,  
    LPCTSTR lpszCategoryNew);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszCategoryOld*  
 若要變更類別名稱。  
  
 [in]*lpszCategoryNew*  
 新的類別名稱。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 類別名稱必須是唯一的。  
  
##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton  
 取代命令的清單方塊中的工具列按鈕上**命令**頁面。  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiCmd*  
 指定要取代的命令按鈕。  
  
 [in]*按鈕*  
 A **const**會取代舊的按鈕的工具列按鈕物件的參考。  
  
### <a name="remarks"></a>備註  
 當[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)， [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)，或[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)新增命令**命令**頁面上，命令會的形式[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件 (或[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)功能表物件包含新增的子功能表項目`AddMenuCommands`)。 架構也會呼叫這三種方法，以自動新增命令。 如果您想要改為以衍生類型的命令時，呼叫`ReplaceButton`並傳入的衍生類型的按鈕。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`ReplaceButton`方法中的`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory  
 指定類別目錄的清單中的類別上**命令**頁面是使用者類別。 您必須呼叫此函式，才能呼叫[CMFCToolBarsCustomizeDialog::Create](#create)。  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszCategory*  
 分類的名稱。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 Framework 目前不使用使用者分類設定。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)

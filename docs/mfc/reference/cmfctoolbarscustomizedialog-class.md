---
title: CMFCToolBarsCustomizeDialog 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: a61cefa7f844062fcca42711ce6515180066b919
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839097"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 類別

無模式索引標籤對話方塊 ( [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)) ，可讓使用者自訂應用程式中的工具列、功能表、鍵盤快速鍵、使用者定義的工具和視覺化樣式。 使用者通常會選取 [ **工具** ] 功能表中的 [ **自訂** ]，以存取這個對話方塊。

[ **自訂** ] 對話方塊有六個索引標籤： **命令**、 **工具列**、 **工具**、 **鍵盤**、 **功能表**和 **選項**。

## <a name="syntax"></a>語法

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog：： CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|建構 `CMFCToolBarsCustomizeDialog` 物件。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)|將工具列按鈕插入 **命令頁面的命令清單** 中|
|[CMFCToolBarsCustomizeDialog：： AddMenu](#addmenu)|從資源載入功能表並呼叫 [CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands) ，將該功能表新增至 **命令** 頁面的命令清單。|
|[CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)|從資源載入功能表並呼叫 [CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands) ，將該功能表新增至 **命令** 頁面的命令清單。|
|[CMFCToolBarsCustomizeDialog：： AddToolBar](#addtoolbar)|從資源載入工具列。 然後，針對功能表中的每個命令呼叫 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton) 方法，以在指定類別下 **命令** 頁面的命令清單中插入按鈕。|
|[CMFCToolBarsCustomizeDialog：： Create](#create)|顯示 [ **自訂** ] 對話方塊。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|
|[CMFCToolBarsCustomizeDialog：： EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|使用 [ **自訂** ] 對話方塊來啟用或停用建立新的工具列。|
|[CMFCToolBarsCustomizeDialog：： FillAllCommandsList](#fillallcommandslist)|`CListBox`使用 [**所有命令**] 分類中的命令，填入提供的物件。|
|[CMFCToolBarsCustomizeDialog：： FillCategoriesComboBox](#fillcategoriescombobox)|`CComboBox`在 [**自訂**] 對話方塊中，以每個命令類別目錄的名稱填入提供的物件。|
|[CMFCToolBarsCustomizeDialog：： FillCategoriesListBox](#fillcategorieslistbox)|`CListBox`在 [**自訂**] 對話方塊中，以每個命令類別目錄的名稱填入提供的物件。|
|[CMFCToolBarsCustomizeDialog：： GetCommandName](#getcommandname)|抓取與指定的命令識別碼相關聯的名稱。|
|[CMFCToolBarsCustomizeDialog：： GetCountInCategory](#getcountincategory)|抓取提供的清單中具有指定之文字標籤的專案數目。|
|[CMFCToolBarsCustomizeDialog：： GetFlags](#getflags)|抓取影響對話方塊行為的旗標集合。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|
|[CMFCToolBarsCustomizeDialog：： OnEditToolbarMenuImage](#onedittoolbarmenuimage)|啟動影像編輯器，讓使用者可以自訂工具列按鈕或功能表項目圖示。|
|[CMFCToolBarsCustomizeDialog：： OnInitDialog](#oninitdialog)|用於擴充屬性工作表初始化的覆寫。  (覆寫 [CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。 ) |
|[CMFCToolBarsCustomizeDialog：:P ostNcDestroy](#postncdestroy)|在視窗已終結之後，由架構呼叫。 (覆寫 `CPropertySheet::PostNcDestroy`。)|
|[CMFCToolBarsCustomizeDialog：： RemoveButton](#removebutton)|從指定的類別或所有類別移除具有指定命令識別碼的按鈕。|
|[CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory)|在 [ **命令** ] 索引標籤的 [類別] 清單方塊中重新命名類別目錄。|
|[CMFCToolBarsCustomizeDialog：： ReplaceButton](#replacebutton)|以新的工具列按鈕物件取代 [ **命令** ] 索引標籤上命令清單中的按鈕。|
|[CMFCToolBarsCustomizeDialog：： SetUserCategory](#setusercategory)|將分類新增至要顯示在 [ **命令** ] 索引標籤上的類別目錄清單。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog：： CheckToolsValidity](#checktoolsvalidity)|由架構呼叫，以判斷使用者定義的工具清單是否有效。|
|[CMFCToolBarsCustomizeDialog：： OnAfterChangeTool](#onafterchangetool)|當使用者定義工具的屬性變更時，由架構呼叫。|
|[CMFCToolBarsCustomizeDialog：： OnAssignKey](#onassignkey)|決定是否可以將指定的鍵盤快速鍵指派給動作。|
|[CMFCToolBarsCustomizeDialog：： OnBeforeChangeTool](#onbeforechangetool)|決定是否可以變更使用者定義的工具。|
|[CMFCToolBarsCustomizeDialog：： OnInitToolsPage](#oninittoolspage)|當使用者選擇 [ **工具** ] 索引標籤時，由架構呼叫。|

## <a name="remarks"></a>備註

若要顯示 [ **自訂** ] 對話方塊，請建立 `CMFCToolBarsCustomizeDialog` 物件，並呼叫 [CMFCToolBarsCustomizeDialog：： create](#create) 方法。

當 [ **自訂** ] 對話方塊處於作用中狀態時，應用程式會以特殊模式運作，以將使用者限制為自訂工作。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarsCustomizeDialog` 類別中使用各種方法。 此範例顯示如何取代 [ **命令** ] 頁面上命令清單方塊中的工具列按鈕、使用 [ **自訂** ] 對話方塊來啟用建立新的工具列，以及顯示 [ **自訂** ] 對話方塊。 此程式碼片段是 [IE 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>規格需求

**標頭：** afxToolBarsCustomizeDialog。h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a> CMFCToolBarsCustomizeDialog：： AddButton

將工具列按鈕插入 **命令頁面的命令清單** 中。

```cpp
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

*uiCategoryId*<br/>
在指定要在其中插入按鈕的分類識別碼。

*按鈕*<br/>
在指定要插入的按鈕。

*iInsertBefore*<br/>
在指定工具列按鈕以零為起始的索引，在該按鈕插入按鈕之前。

*lpszCategory*<br/>
在指定要插入按鈕的類別目錄字串。

### <a name="remarks"></a>備註

`AddButton`方法會忽略具有標準命令識別碼的按鈕 (例如 ID_FILE_MRU_FILE1) 、不允許的命令 (請參閱[CMFCToolBar：： IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虛擬按鈕。

這個方法會建立相同型別的新物件， `button` (通常是使用按鈕的 runtime 類別) 的 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md) 。 然後，它會呼叫 [CMFCToolBarButton：： CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) 來複製按鈕的資料成員，然後將複本插入指定的類別中。

插入新的按鈕時，會收到 `OnAddToCustomizePage` 通知。

如果 `iInsertBefore` 為-1，則按鈕會附加至類別清單，否則會插入具有指定索引的專案之前。

### <a name="example"></a>範例

下列範例示範如何使用 `AddButton` 類別的方法 `CMFCToolBarsCustomizeDialog` 。 此程式碼片段是 [滑杆範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a> CMFCToolBarsCustomizeDialog：： AddMenu

從資源載入功能表並呼叫 [CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands) ，將該功能表新增至 **命令** 頁面的命令清單。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuResId*<br/>
在指定要載入之功能表的資源識別碼。

### <a name="return-value"></a>傳回值

如果已成功加入功能表，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

在的呼叫中 `AddMenuCommands` ， *BPOPUP* 是 FALSE。 因此，該方法不會將包含子功能表的功能表項目加入至命令清單中。 這個方法會將子功能表中的功能表項目新增至命令清單。

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a> CMFCToolBarsCustomizeDialog：： AddMenuCommands

將專案新增至 **命令** 頁面中的命令清單，以代表指定之功能表中的所有專案。

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
在要加入之 CMenu 物件的指標。

*bPopup*<br/>
在指定是否要將快捷方式功能表項目插入命令清單中。

*lpszCategory*<br/>
在要插入功能表的類別目錄名稱。

*lpszMenuPath*<br/>
在在 [ **所有類別** ] 清單中顯示命令時，新增至名稱的前置詞。

### <a name="remarks"></a>備註

方法會在 `AddMenuCommands` *pMenu*的所有功能表項目上迴圈。 對於不包含子功能表的每個功能表項目，此方法會建立 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md) 物件，並呼叫 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton) 方法，以將功能表項目加入至 **命令** 頁面上命令清單的工具列按鈕。 此進程會忽略分隔符號。

如果 *bPopup* 為 TRUE，則此方法會針對包含子功能表的每個功能表項目建立 [CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md) 物件，並藉由呼叫將其插入命令清單中 `AddButton` 。 否則，在命令清單中不會顯示包含子功能表的功能表項目。 在任一種情況下，當 `AddMenuCommands` 遇到具有子功能表的功能表項目時，它會以遞迴方式呼叫它，並將子功能表的指標以 *pMenu* 參數傳遞，並將子功能表的標籤附加至 *lpszMenuPath*。

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a> CMFCToolBarsCustomizeDialog：： AddToolBar

從資源載入工具列。 然後，針對功能表中的每個命令呼叫 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton) 方法，以在指定類別下 **命令** 頁面的命令清單中插入按鈕。

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>參數

*uiCategoryId*<br/>
在指定要加入工具列之類別的資源識別碼。

*uiToolbarResId*<br/>
在指定工具列的資源識別碼，其命令會插入命令清單中。

*lpszCategory*<br/>
在指定要加入工具列的類別目錄名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="example"></a>範例

下列範例示範如何使用 `AddToolBar` 類別中的方法 `CMFCToolBarsCustomizeDialog` 。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>備註

用來表示每個命令的控制項是 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md) 物件。 加入工具列之後，您可以藉由呼叫 [CMFCToolBarsCustomizeDialog：： ReplaceButton](#replacebutton)，將按鈕取代為衍生類型的控制項。

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a> CMFCToolBarsCustomizeDialog：： CheckToolsValidity

驗證使用者工具清單的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>參數

*lstTools*<br/>
在要檢查的使用者定義工具清單。

### <a name="return-value"></a>傳回值

如果使用者定義的工具清單是有效的，則傳回 TRUE;否則為 FALSE。 預設的實值一律會傳回 TRUE。

### <a name="remarks"></a>備註

架構會呼叫這個方法，以確認代表 [CMFCToolBarsCustomizeDialog：： CheckToolsValidity](#checktoolsvalidity)所傳回之使用者定義工具的物件有效性。

`CheckToolsValidity` `CMFCToolBarsCustomizeDialog` 如果您想要在使用者關閉對話方塊之前驗證使用者工具，請覆寫衍生自之類別中的方法。 如果當使用者按一下對話方塊右上角的 [ **關閉** ] 按鈕或對話方塊右下角標示 [ **關閉** ] 按鈕時，這個方法會傳回 FALSE，則對話方塊會顯示 [ **工具** ] 索引標籤，而不是 [關閉]。 如果當使用者按一下索引標籤離開 [ **工具** ] 索引標籤時，這個方法會傳回 FALSE，則不會進行導覽。 您應該會顯示適當的訊息方塊，通知使用者導致驗證失敗的問題。

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a> CMFCToolBarsCustomizeDialog：： CMFCToolBarsCustomizeDialog

建構 `CMFCToolBarsCustomizeDialog` 物件。

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>參數

*pWndParentFrame*<br/>
在父框架的指標。 此參數不得為 Null。

*bAutoSetFromMenus*<br/>
在布林值，指定是否要在 [ **命令** ] 頁面的命令清單中，加入所有功能表的功能表命令。 如果此參數為 TRUE，則會加入功能表命令。 否則，不會加入功能表命令。

*uiFlags*<br/>
在影響對話方塊行為的旗標組合。 這個參數可以是下列其中一個或多個值：

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
在 `CRuntimeClass` 指定其他自訂頁面之物件清單的指標。

### <a name="remarks"></a>備註

*PlistCustomPages*參數 `CRuntimeClass` 會參考指定其他自訂頁面的物件清單。 此函式會使用 [CRuntimeClass：： CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) 方法，在對話方塊中新增更多頁面。 如需將其他頁面新增至 [ **自訂** ] 對話方塊的範例，請參閱 CustomPages 範例。

如需您可以在 *uiFlags* 參數中傳遞之值的詳細資訊，請參閱 [CMFCToolBarsCustomizeDialog：： GetFlags](#getflags)。

### <a name="example"></a>範例

下列範例示範如何建立類別的物件 `CMFCToolBarsCustomizeDialog` 。 此程式碼片段是 [自訂頁面範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a> CMFCToolBarsCustomizeDialog：： Create

顯示 [ **自訂** ] 對話方塊。

```
virtual BOOL Create();
```

### <a name="return-value"></a>傳回值

如果成功建立自訂屬性工作表，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

請在 `Create` 完全初始化類別之後，才呼叫方法。

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a> CMFCToolBarsCustomizeDialog：： EnableUserDefinedToolbars

使用 [ **自訂** ] 對話方塊來啟用或停用建立新的工具列。

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用使用者定義的工具列;FALSE 表示停用工具列。

### <a name="remarks"></a>備註

如果 *bEnable* 為 TRUE，[ **新增**]、[ **重新命名** ] 和 [ **刪除** ] 按鈕會顯示在 [ **工具列** ] 頁面上。

依預設，或如果 *bEnable* 為 FALSE，則不會顯示這些按鈕，使用者也無法定義新的工具列。

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a> CMFCToolBarsCustomizeDialog：： FillAllCommandsList

`CListBox`使用 [**所有命令**] 分類中的命令，填入提供的物件。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>參數

*wndListOfCommands*<br/>
擴展 `CListBox` 要填入之物件的參考。

### <a name="remarks"></a>備註

**所有命令**類別都包含所有類別的命令。 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton)方法會為您將與提供之按鈕相關聯的命令新增至 [**所有命令**] 類別。

這個方法會先清除所提供物件的內容， `CListBox` 然後再使用 [ **所有命令** ] 類別目錄中的命令填入該物件。

`CMFCMousePropertyPage`類別會使用此方法來填入 [按兩下事件] 清單方塊。

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a> CMFCToolBarsCustomizeDialog：： FillCategoriesComboBox

`CComboBox`在 [**自訂**] 對話方塊中，以每個命令類別目錄的名稱填入提供的物件。

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
擴展 `CComboBox` 要填入之物件的參考。

*bAddEmpty*<br/>
在布林值，指定是否要將分類加入沒有命令的下拉式方塊。 如果此參數為 TRUE，則會將空白類別新增至下拉式方塊。 否則，不會新增空白的分類。

### <a name="remarks"></a>備註

這個方法就像是 [CMFCToolBarsCustomizeDialog：： FillCategoriesListBox](#fillcategorieslistbox) 方法，但這個方法會搭配 `CComboBox` 物件運作。

在填入物件之前，這個方法不會清除該物件的內容 `CComboBox` 。 它保證 **所有命令** 類別目錄都是下拉式方塊中的最後一個專案。

您可以使用 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton) 方法來加入新的命令類別目錄。 您可以使用 [CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory) 方法來變更現有類別的名稱。

`CMFCToolBarsKeyboardPropertyPage`和 `CMFCKeyMapDialog` 類別會使用此方法將鍵盤對應分類。

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a> CMFCToolBarsCustomizeDialog：： FillCategoriesListBox

`CListBox`在 [**自訂**] 對話方塊中，以每個命令類別目錄的名稱填入提供的物件。

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
擴展 `CListBox` 要填入之物件的參考。

*bAddEmpty*<br/>
在布林值，指定是否要在沒有命令的清單方塊中加入分類。 如果此參數為 TRUE，就會在清單方塊中加入空的分類。 否則，不會新增空白的分類。

### <a name="remarks"></a>備註

這個方法就像是 [CMFCToolBarsCustomizeDialog：： FillCategoriesComboBox](#fillcategoriescombobox) 方法，但這個方法會搭配 `CListBox` 物件運作。

在填入物件之前，這個方法不會清除該物件的內容 `CListBox` 。 它保證 **所有命令** 類別目錄都是清單方塊中的最後一個專案。

您可以使用 [CMFCToolBarsCustomizeDialog：： AddButton](#addbutton) 方法來加入新的命令類別目錄。 您可以使用 [CMFCToolBarsCustomizeDialog：： RenameCategory](#renamecategory) 方法來變更現有類別的名稱。

`CMFCToolBarsCommandsPropertyPage`類別會使用此方法來顯示與每個命令類別目錄相關聯的命令清單。

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a> CMFCToolBarsCustomizeDialog：： GetCommandName

抓取與指定的命令識別碼相關聯的名稱。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在要取出的命令識別碼。

### <a name="return-value"></a>傳回值

與指定的命令識別碼相關聯的名稱，如果命令不存在，則為 Null。

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a> CMFCToolBarsCustomizeDialog：： GetCountInCategory

抓取提供的清單中具有指定之文字標籤的專案數目。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
在要比對的文字標籤。

*lstCommands*<br/>
在包含物件之清單的參考 `CMFCToolBarButton` 。

### <a name="return-value"></a>傳回值

提供清單中的專案數，其文字標籤等於 *lpszItemName*。

### <a name="remarks"></a>備註

提供之物件清單中的每個元素都必須是類型 `CMFCToolBarButton` 。 這個方法會比較 *lpszItemName* 與 [CMFCToolBarButton：： m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) 資料成員。

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a> CMFCToolBarsCustomizeDialog：： GetFlags

抓取影響對話方塊行為的旗標集合。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>傳回值

影響對話方塊行為的旗標集合。

### <a name="remarks"></a>備註

這個方法會抓取傳遞給函式的 *uiFlags* 參數值。 傳回值可以是下列一或多個值：

|名稱|描述|
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|允許使用者指定功能表的陰影外觀。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允許使用者指定是否要在工具列按鈕影像下方顯示文字標籤。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允許使用者指定功能表動畫樣式。  |
|AFX_CUSTOMIZE_NOHELP|移除 [自訂] 對話方塊中的 [說明] 按鈕。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|啟用 WS_EX_CONTEXTHELP 視覺效果樣式。  |
|AFX_CUSTOMIZE_NOTOOLS|移除 [自訂] 對話方塊中的 [ **工具** ] 頁面。 如果您的應用程式使用類別，此旗標會是有效的 `CUserToolsManager` 。  |
|AFX_CUSTOMIZE_MENUAMPERS|允許按鈕標題包含 () 字元的連字號 **&** 。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|從 [自訂] 對話方塊中移除 **大型圖示** 選項。  |

如需 WS_EX_CONTEXTHELP 視覺化樣式的詳細資訊，請參閱 [擴充的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a> CMFCToolBarsCustomizeDialog：： OnAfterChangeTool

在使用者工具發生之後立即回應變更。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in，out]已變更之使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者變更使用者定義工具的屬性時，架構會呼叫這個方法。 預設實作不做任何動作。 在衍生自的類別中覆寫這個方法 `CMFCToolBarsCustomizeDialog`  ，以便在使用者工具變更發生之後執行處理。

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a> CMFCToolBarsCustomizeDialog：： OnAssignKey

當使用者定義鍵盤快速鍵時進行驗證。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>參數

*pAccel*<br/>
[in，out]表示為 [ACCEL](/windows/win32/api/winuser/ns-winuser-accel) 結構之建議鍵盤指派的指標。

### <a name="return-value"></a>傳回值

如果可以指派金鑰，則為 TRUE; 如果無法指派金鑰，則為 FALSE。 預設的實值一律會傳回 TRUE。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以便在使用者指派新的鍵盤快速鍵時執行額外的處理，或是在使用者定義鍵盤快速鍵時，驗證鍵盤快速鍵。 若要防止指派快捷方式，則傳回 FALSE。 您也應該會顯示訊息方塊，或通知使用者鍵盤快速鍵被拒的原因。

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a> CMFCToolBarsCustomizeDialog：： OnBeforeChangeTool

當使用者即將套用變更時，對使用者工具進行變更時，就會執行自訂處理。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in，out]即將被取代之使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者定義工具的屬性即將變更時，架構會呼叫這個方法。 預設實作不做任何動作。 `OnBeforeChangeTool` `CMFCToolBarsCustomizeDialog` 如果您想要在使用者工具變更發生之前執行處理，例如釋放*pSelTool*使用的資源，請覆寫衍生自之類別中的方法。

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a> CMFCToolBarsCustomizeDialog：： OnEditToolbarMenuImage

啟動影像編輯器，讓使用者可以自訂工具列按鈕或功能表項目圖示。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在父視窗的指標。

*點陣圖*<br/>
在要編輯之點陣圖物件的參考。

*nBitsPerPixel*<br/>
在點陣圖色彩解析度（以位/圖元為單位）。

### <a name="return-value"></a>傳回值

如果正在認可變更，則為 TRUE;否則為 FALSE。 預設的執行會顯示對話方塊，並在使用者按一下 **[確定]** 時傳回 TRUE; 如果使用者按一下 [ **取消** ] 或 [ **關閉** ] 按鈕，則傳回 FALSE。

### <a name="remarks"></a>備註

當使用者執行影像編輯器時，架構會呼叫這個方法。 預設的執行會顯示 [ [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md) ] 對話方塊。 覆寫 `OnEditToolbarMenuImage` 衍生類別中的，以使用自訂影像編輯器。

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a> CMFCToolBarsCustomizeDialog：： OnInitDialog

用於擴充屬性工作表初始化的覆寫。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

呼叫 [CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) 方法的結果。

### <a name="remarks"></a>備註

這個方法會藉由顯示 [**關閉**] 按鈕，藉由確定對話方塊是否符合目前的螢幕大小，**以及將 [說明] 按鈕移**至對話方塊的左下角，來擴充基類實[CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a> CMFCToolBarsCustomizeDialog：： OnInitToolsPage

處理 **工具** 頁面即將初始化的架構通知。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>備註

預設實作不做任何動作。 在衍生類別中覆寫此方法以處理此通知。

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a> CMFCToolBarsCustomizeDialog：:P ostNcDestroy

在視窗已終結之後，由架構呼叫。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>備註

這個方法會藉 `CPropertySheet::PostNcDestroy` 由將應用程式還原為先前的模式，來擴充基類的實作為。

[CMFCToolBarsCustomizeDialog：： Create](#create)方法會將應用程式置於特殊模式，以將使用者限制為自訂工作。

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a> CMFCToolBarsCustomizeDialog：： RemoveButton

從指定的類別或所有類別移除具有指定命令識別碼的按鈕。

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>參數

*uiCategoryId*<br/>
在指定要從中移除按鈕的類別目錄識別碼。

*uiCmdId*<br/>
在指定按鈕的命令識別碼。

*lpszCategory*<br/>
在指定要從中移除按鈕的類別目錄名稱。

### <a name="return-value"></a>傳回值

移除之按鈕的以零為起始的索引，如果在指定的類別目錄中找不到指定的命令識別碼，則為-1。 如果 *uiCategoryId* 為-1，則傳回值為0。

### <a name="remarks"></a>備註

若要移除所有類別中的按鈕，請呼叫這個方法的第一個多載，並將 *uiCategoryId* 設定為-1。

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a> CMFCToolBarsCustomizeDialog：： RenameCategory

在 [ **命令** ] 頁面的 [類別目錄] 清單方塊中重新命名類別目錄。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>參數

*lpszCategoryOld*<br/>
在要變更的分類名稱。

*lpszCategoryNew*<br/>
在新的分類名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

類別目錄名稱必須是唯一的。

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a> CMFCToolBarsCustomizeDialog：： ReplaceButton

取代 **命令** 頁面上命令清單方塊中的工具列按鈕。

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在指定要取代之按鈕的命令。

*按鈕*<br/>
在 **`const`** 取代舊按鈕之工具列按鈕物件的參考。

### <a name="remarks"></a>備註

當 [CMFCToolBarsCustomizeDialog：： AddMenu](#addmenu)、 [CMFCToolBarsCustomizeDialog：： AddMenuCommands](#addmenucommands)或 [CMFCToolBarsCustomizeDialog：： AddToolBar](#addtoolbar) 將命令加入至 [ **命令** ] 頁面時，該命令會以 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md) 物件的形式 (或包含) 所新增之子功能表的功能表項目的 [CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md) 物件 `AddMenuCommands` 。 架構也會呼叫這三個方法，以自動新增命令。 如果您想要改為以衍生型別表示命令，請呼叫 `ReplaceButton` 並傳入衍生型別的按鈕。

### <a name="example"></a>範例

下列範例示範如何使用 `ReplaceButton` 類別中的方法 `CMFCToolBarsCustomizeDialog` 。 此程式碼片段是 [Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a> CMFCToolBarsCustomizeDialog：： SetUserCategory

在 [ **命令** ] 頁面上，指定類別清單中的哪一個分類為 [使用者] 類別。 您必須先呼叫此函式，才能呼叫 [CMFCToolBarsCustomizeDialog：： Create](#create)。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>參數

*lpszCategory*<br/>
在分類的名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

架構目前不會使用使用者類別設定。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)

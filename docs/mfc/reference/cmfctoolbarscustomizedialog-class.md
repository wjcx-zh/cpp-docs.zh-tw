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
ms.openlocfilehash: 239532c78491f121423ca42a2c3dfc306997c841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504682"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 類別

無模式索引標籤對話方塊 ( [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)), 可讓使用者自訂應用程式中的工具列、功能表、鍵盤快速鍵、使用者定義的工具和視覺化樣式。 使用者通常會選取 [ **工具** ] 功能表中的 [ **自訂** ]，以存取這個對話方塊。

[**自訂**] 對話方塊有六個索引標籤:**命令**、**工具列**、**工具**、**鍵盤**、**功能表**和**選項**。

## <a name="syntax"></a>語法

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|建構 `CMFCToolBarsCustomizeDialog` 物件。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|在 [**命令**] 頁面上的命令清單中插入工具列按鈕|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu)|從資源載入功能表並呼叫[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) , 將該功能表新增至 [**命令**] 頁面上的命令清單。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)|從資源載入功能表並呼叫[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) , 將該功能表新增至 [**命令**] 頁面上的命令清單。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)|從資源載入工具列。 然後, 針對功能表中的每個命令呼叫[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法, 在命令頁面的命令清單中, 于指定的類別下插入一個按鈕。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: Create](#create)|顯示 [**自訂**] 對話方塊。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|使用 [**自訂**] 對話方塊來啟用或停用建立新的工具列。|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|使用 [ `CListBox` **所有命令**] 分類中的命令填入提供的物件。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|在 [ `CComboBox` **自訂**] 對話方塊中, 以每個命令類別的名稱填入提供的物件。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|在 [ `CListBox` **自訂**] 對話方塊中, 以每個命令類別的名稱填入提供的物件。|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|抓取與指定的命令識別碼相關聯的名稱。|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|抓取提供的清單中具有指定文字標籤的專案數。|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|抓取會影響對話方塊行為的旗標集合。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage](#onedittoolbarmenuimage)|啟動影像編輯器, 讓使用者可以自訂工具列按鈕或功能表項目圖示。|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|覆寫以擴大屬性工作表初始化。 (覆寫[CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|在終結視窗之後, 由架構呼叫。 (覆寫 `CPropertySheet::PostNcDestroy`。)|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: RemoveButton](#removebutton)|從指定的分類或從所有類別移除具有指定命令識別碼的按鈕。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)|在 [**命令**] 索引標籤上, 重新命名類別清單方塊中的類別。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)|以新的工具列按鈕物件取代 [**命令**] 索引標籤上的命令清單中的按鈕。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: SetUserCategory](#setusercategory)|將分類新增至將顯示在 [**命令**] 索引標籤上的類別目錄清單。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)|由架構呼叫以判斷使用者定義的工具清單是否有效。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAfterChangeTool](#onafterchangetool)|當使用者定義工具的屬性變更時, 由架構呼叫。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnAssignKey](#onassignkey)|決定是否可以將指定的鍵盤快速鍵指派給某個動作。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool](#onbeforechangetool)|判斷使用者定義的工具是否可以變更。|
|`CMFCToolBarsCustomizeDialog::`[CMFCToolBarsCustomizeDialog:: OnInitToolsPage](#oninittoolspage)|當使用者選擇 [**工具**] 索引標籤時, 由架構呼叫。|

## <a name="remarks"></a>備註

若要顯示 [**自訂**] 對話方塊, `CMFCToolBarsCustomizeDialog`請建立物件, 並呼叫[CMFCToolBarsCustomizeDialog:: create](#create)方法。

當 [**自訂**] 對話方塊處於作用中狀態時, 應用程式會以特殊模式運作, 將使用者限制為自訂工作。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarsCustomizeDialog` 類別中使用各種方法。 此範例示範如何取代 [**命令**] 頁面上命令清單方塊中的工具列按鈕、使用 [**自訂**] 對話方塊來啟用建立新的工具列, 以及顯示 [**自訂**] 對話方塊。 此程式碼片段是[IE 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>需求

**標頭:** afxToolBarsCustomizeDialog。h

##  <a name="addbutton"></a>CMFCToolBarsCustomizeDialog:: AddButton

在 [**命令**] 頁面上的命令清單中插入工具列按鈕。

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

*uiCategoryId*<br/>
在指定要在其中插入按鈕的分類識別碼。

*button*<br/>
在指定要插入的按鈕。

*iInsertBefore*<br/>
在指定在插入按鈕之前, 工具列按鈕以零為起始的索引。

*lpszCategory*<br/>
在指定要插入按鈕的類別字串。

### <a name="remarks"></a>備註

方法會忽略具有標準命令 id (例如 ID_FILE_MRU_FILE1) 的按鈕、不允許的命令 (請參閱[CMFCToolBar:: IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虛擬按鈕。 `AddButton`

這個方法會使用按鈕的 runtime 類別, 建立和`button` (通常是[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)) 相同類型的新物件。 接著, 它會呼叫[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)來複製按鈕的資料成員, 並將該複本插入指定的分類中。

插入 [新增] 按鈕時, 它會接收`OnAddToCustomizePage`通知。

如果`iInsertBefore`為-1, 則按鈕會附加至分類清單, 否則會插入具有指定索引的專案之前。

### <a name="example"></a>範例

下列範例示範如何使用`AddButton` `CMFCToolBarsCustomizeDialog`類別的方法。 此程式碼片段是[滑杆範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog:: AddMenu

從資源載入功能表並呼叫[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands) , 將該功能表新增至 [**命令**] 頁面上的命令清單。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuResId*<br/>
在指定要載入之功能表的資源識別碼。

### <a name="return-value"></a>傳回值

如果已成功新增功能表, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

在的呼叫`AddMenuCommands`中, *bPopup*是 FALSE。 因此, 該方法不會將包含子功能表的功能表項目加入至命令清單。 這個方法會將子功能表中的功能表項目新增至命令清單。

##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog:: AddMenuCommands

將專案新增至 [**命令**] 頁面中的命令清單, 以表示指定功能表中的所有專案。

```
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
在指定是否要將快顯功能表專案插入命令清單。

*lpszCategory*<br/>
在要插入功能表的類別目錄名稱。

*lpszMenuPath*<br/>
在當命令顯示在 [**所有類別**] 清單中時, 新增至名稱的前置詞。

### <a name="remarks"></a>備註

方法會對 pMenu 的所有功能表項目進行迴圈。 `AddMenuCommands` 針對每個不包含子功能表的功能表項目, 此方法會建立[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件, 並呼叫[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法, 將功能表項目當做工具列按鈕加入至命令**清單命令**頁面。 在此進程中會忽略分隔符號。

如果*bPopup*為 TRUE, 則針對每個包含子功能表的功能表項目, 此方法會建立[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件, 並藉由呼叫`AddButton`將其插入命令清單中。 否則, 包含子功能表的功能表項目不會顯示在命令清單中。 不論是哪一種`AddMenuCommands`情況, 當遇到具有子功能表的功能表項目時, 它會以遞迴方式呼叫它本身, 傳遞子功能表的指標做為*pMenu*參數, 並將子功能表的標籤附加至*lpszMenuPath*。

##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog:: AddToolBar

從資源載入工具列。 然後, 針對功能表中的每個命令呼叫[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法, 在命令頁面的命令清單中, 于指定的類別下插入一個按鈕。

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
在指定要加入工具列之類別目錄的資源識別碼。

*uiToolbarResId*<br/>
在指定工具列的資源識別碼, 其命令會插入命令清單中。

*lpszCategory*<br/>
在指定要加入工具列的類別目錄名稱。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="example"></a>範例

下列範例示範如何`AddToolBar` `CMFCToolBarsCustomizeDialog`在類別中使用方法。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>備註

用來代表每個命令的控制項是[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件。 加入工具列之後, 您可以藉由呼叫[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton), 將按鈕取代為衍生類型的控制項。

##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog:: CheckToolsValidity

驗證使用者工具清單的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>參數

*lstTools*<br/>
在要檢查的使用者定義工具清單。

### <a name="return-value"></a>傳回值

如果使用者定義的工具清單有效, 則傳回 TRUE;否則為 FALSE。 預設的執行一律會傳回 TRUE。

### <a name="remarks"></a>備註

架構會呼叫這個方法, 以驗證代表[CMFCToolBarsCustomizeDialog:: CheckToolsValidity](#checktoolsvalidity)傳回之使用者定義工具的物件是否有效。

如果您`CheckToolsValidity`想要在使用者關閉對話方塊`CMFCToolBarsCustomizeDialog`之前驗證使用者工具, 請覆寫衍生自之類別中的方法。 當使用者按一下對話方塊右上角的 [**關閉**] 按鈕, 或對話方塊右下角標示為 [**關閉**] 的按鈕時, 如果這個方法傳回 FALSE, 對話方塊就會顯示 [**工具**] 索引標籤, 而不是閉合. 如果當使用者按一下索引標籤以離開 [**工具**] 索引標籤時, 這個方法會傳回 FALSE, 則不會進行導覽。 您應該會顯示適當的訊息方塊, 通知使用者導致驗證失敗的問題。

##  <a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog

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
在布林值, 指定是否要將功能表命令從所有功能表新增至 [**命令**] 頁面上的命令清單。 如果此參數為 TRUE, 則會加入功能表命令。 否則, 不會加入功能表命令。

*uiFlags*<br/>
在會影響對話方塊行為的旗標組合。 這個參數可以是下列一個或多個值:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
在指定其他自訂頁面之`CRuntimeClass`物件清單的指標。

### <a name="remarks"></a>備註

*PlistCustomPages*參數會參考指定其他自訂`CRuntimeClass`頁面的物件清單。 此函式會使用[CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法, 在對話方塊中加入更多頁面。 如需在 [**自訂**] 對話方塊中加入更多頁面的範例, 請參閱 CustomPages 範例。

如需您可以在*uiFlags*參數中傳遞之值的詳細資訊, 請參閱[CMFCToolBarsCustomizeDialog:: GetFlags](#getflags)。

### <a name="example"></a>範例

下列範例示範如何建立`CMFCToolBarsCustomizeDialog`類別的物件。 此程式碼片段是[自訂頁面範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>CMFCToolBarsCustomizeDialog:: Create

顯示 [**自訂**] 對話方塊。

```
virtual BOOL Create();
```

### <a name="return-value"></a>傳回值

如果已成功建立自訂屬性工作表, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

只有在您完全初始化類別之後, 才呼叫方法。`Create`

##  <a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog:: EnableUserDefinedToolbars

使用 [**自訂**] 對話方塊來啟用或停用建立新的工具列。

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用使用者定義的工具列;FALSE 表示停用工具列。

### <a name="remarks"></a>備註

如果*bEnable*為 TRUE, [**新增**]、[**重新命名**] 和 [**刪除**] 按鈕會顯示在 [**工具列**] 頁面上。

根據預設, 或如果*bEnable*為 FALSE, 則不會顯示這些按鈕, 而且使用者無法定義新的工具列。

##  <a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog:: FillAllCommandsList

使用 [ `CListBox` **所有命令**] 分類中的命令填入提供的物件。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>參數

*wndListOfCommands*<br/>
脫銷要填入之`CListBox`物件的參考。

### <a name="remarks"></a>備註

[**所有命令**] 類別包含所有類別的命令。 [CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法會將與所提供按鈕相關聯的命令加入至 [**所有命令**] 分類。

這個方法會先清除所提供`CListBox`物件的內容, 再以 [**所有命令**] 分類中的命令填入。

`CMFCMousePropertyPage`類別會使用這個方法來填入 [按兩下事件] 清單方塊。

##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox

在 [ `CComboBox` **自訂**] 對話方塊中, 以每個命令類別的名稱填入提供的物件。

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
脫銷要填入之`CComboBox`物件的參考。

*bAddEmpty*<br/>
在布林值, 指定是否要將分類加入沒有命令的下拉式方塊。 如果此參數為 TRUE, 則會將空的分類新增至下拉式方塊。 否則, 不會加入空的類別目錄。

### <a name="remarks"></a>備註

這個方法類似于[CMFCToolBarsCustomizeDialog:: FillCategoriesListBox](#fillcategorieslistbox)方法, 不同之處在于這個方法適用`CComboBox`于物件。

這個方法不會在填入`CComboBox`物件之前清除其內容。 它保證 [**所有命令**] 類別目錄是下拉式方塊中的最後一個專案。

您可以使用[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法來加入新的命令類別目錄。 您可以使用[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)方法來變更現有分類的名稱。

`CMFCToolBarsKeyboardPropertyPage` 和`CMFCKeyMapDialog`類別會使用這個方法來分類鍵盤對應。

##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog:: FillCategoriesListBox

在 [ `CListBox` **自訂**] 對話方塊中, 以每個命令類別的名稱填入提供的物件。

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
脫銷要填入之`CListBox`物件的參考。

*bAddEmpty*<br/>
在布林值, 指定是否要將分類加入沒有命令的清單方塊。 如果此參數為 TRUE, 則會將空的分類新增至清單方塊。 否則, 不會加入空的類別目錄。

### <a name="remarks"></a>備註

這個方法類似于[CMFCToolBarsCustomizeDialog:: FillCategoriesComboBox](#fillcategoriescombobox)方法, 不同之處在于這個方法適用`CListBox`于物件。

這個方法不會在填入`CListBox`物件之前清除其內容。 它保證 [**所有命令**] 類別目錄是清單方塊中的最後一個專案。

您可以使用[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)方法來加入新的命令類別目錄。 您可以使用[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)方法來變更現有分類的名稱。

`CMFCToolBarsCommandsPropertyPage`類別會使用這個方法來顯示與每個命令類別目錄相關聯的命令清單。

##  <a name="getcommandname"></a>CMFCToolBarsCustomizeDialog:: GetCommandName

抓取與指定的命令識別碼相關聯的名稱。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在要取出的命令識別碼。

### <a name="return-value"></a>傳回值

與指定的命令識別碼相關聯的名稱, 如果命令不存在, 則為 Null。

##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog:: GetCountInCategory

抓取提供的清單中具有指定文字標籤的專案數。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
在要比對的文字標籤。

*lstCommands*<br/>
在包含`CMFCToolBarButton`物件之清單的參考。

### <a name="return-value"></a>傳回值

提供的清單中, 其文字標籤等於*lpszItemName*的專案數。

### <a name="remarks"></a>備註

所提供之物件清單中的每個專案都`CMFCToolBarButton`必須是型別。 這個方法會比較*lpszItemName*與[CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)資料成員。

##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog:: GetFlags

抓取會影響對話方塊行為的旗標集合。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>傳回值

一組會影響對話方塊行為的旗標。

### <a name="remarks"></a>備註

這個方法會抓取傳遞給此函式的*uiFlags*參數值。 傳回值可以是下列一個或多個值:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|允許使用者指定功能表的陰影外觀。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允許使用者指定是否要在工具列按鈕影像下方顯示文字標籤。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允許使用者指定功能表動畫樣式。  |
|AFX_CUSTOMIZE_NOHELP|移除 [自訂] 對話方塊中的 [說明] 按鈕。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|啟用 WS_EX_CONTEXTHELP 視覺化樣式。  |
|AFX_CUSTOMIZE_NOTOOLS|從 [自訂] 對話方塊中移除 [**工具**] 頁面。 如果您的應用程式使用類別, 則`CUserToolsManager`此旗標是有效的。  |
|AFX_CUSTOMIZE_MENUAMPERS|允許按鈕標題包含連字號 ( **&** ) 字元。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|從 [自訂] 對話方塊中移除 [**大型圖示**] 選項。  |

如需 WS_EX_CONTEXTHELP 視覺化樣式的詳細資訊, 請參閱[擴充的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

##  <a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog:: OnAfterChangeTool

在使用者工具發生後立即回應變更。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in、out]已變更之使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者變更使用者定義工具的屬性時, 架構會呼叫這個方法。 預設實作不做任何動作。 在衍生自`CMFCToolBarsCustomizeDialog`的類別中覆寫這個方法, 以在使用者工具發生變更之後執行處理。

##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog:: OnAssignKey

在使用者定義鍵盤快速鍵時進行驗證。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>參數

*pAccel*<br/>
[in、out]以[ACCEL](/windows/win32/api/winuser/ns-winuser-accel)結構表示之提議鍵盤指派的指標。

### <a name="return-value"></a>傳回值

如果可以指派金鑰, 則為 TRUE, 如果無法指派金鑰, 則為 FALSE。 預設的執行一律會傳回 TRUE。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以在使用者指派新的鍵盤快速鍵時執行額外的處理, 或在使用者定義鍵盤快速鍵時進行驗證。 若要防止指派快捷方式, 請傳回 FALSE。 您也應該顯示訊息方塊, 或通知使用者鍵盤快速鍵遭到拒絕的原因。

##  <a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool

當使用者即將套用變更時, 會執行自訂處理。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in、out]即將取代之使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者定義工具的屬性即將變更時, 架構會呼叫這個方法。 預設實作不做任何動作。 如果您`OnBeforeChangeTool`想要在使用者工具發生`CMFCToolBarsCustomizeDialog`變更之前執行處理, 例如釋放*pSelTool*使用的資源, 請覆寫衍生自之類別中的方法。

##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage

啟動影像編輯器, 讓使用者可以自訂工具列按鈕或功能表項目圖示。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在父視窗的指標。

*bitmap*<br/>
在要編輯之點陣圖物件的參考。

*nBitsPerPixel*<br/>
在點陣圖色彩解析度 (以位/圖元為單位)。

### <a name="return-value"></a>傳回值

如果正在認可變更, 則為 TRUE;否則為 FALSE。 預設的執行會顯示一個對話方塊, 如果使用者按一下 **[確定**], 則會傳回 TRUE, 如果使用者按一下 [**取消**] 或 [**關閉**] 按鈕, 則會傳回 FALSE。

### <a name="remarks"></a>備註

當使用者執行影像編輯器時, 架構會呼叫這個方法。 預設的 [執行] 會顯示 [ [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)] 對話方塊。 覆`OnEditToolbarMenuImage`寫衍生類別中的, 以使用自訂影像編輯器。

##  <a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog:: OnInitDialog

覆寫以擴大屬性工作表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

呼叫[CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法的結果。

### <a name="remarks"></a>備註

這個方法會藉由顯示 [**關閉**] 按鈕來擴充基類實值 ( [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)), 方法是確定對話方塊符合目前的螢幕大小, 並將 [說明 ] 按鈕移至左下角對話方塊的。

##  <a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog:: OnInitToolsPage

處理**工具**頁面即將初始化之架構的通知。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>備註

預設實作不做任何動作。 覆寫衍生類別中的這個方法, 以處理此通知。

##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::P ostNcDestroy

在終結視窗之後, 由架構呼叫。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>備註

這個方法會藉由將應用程式`CPropertySheet::PostNcDestroy`還原為先前的模式, 來擴充基類的執行。

[CMFCToolBarsCustomizeDialog:: Create](#create)方法會將應用程式置於特殊模式, 以限制使用者自訂工作。

##  <a name="removebutton"></a>CMFCToolBarsCustomizeDialog:: RemoveButton

從指定的分類或從所有類別移除具有指定命令識別碼的按鈕。

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
[in]指定要從中移除按鈕的類別目錄識別碼。

*uiCmdId*<br/>
在指定按鈕的命令 ID。

*lpszCategory*<br/>
[in]指定要從中移除按鈕的類別目錄的名稱。

### <a name="return-value"></a>傳回值

已移除按鈕之以零為起始的索引, 如果在指定的分類中找不到指定的命令 ID, 則為-1。 如果*uiCategoryId*為-1, 則傳回值為0。

### <a name="remarks"></a>備註

若要移除所有類別的按鈕, 請呼叫這個方法的第一個多載, 並將*uiCategoryId*設定為-1。

##  <a name="renamecategory"></a>CMFCToolBarsCustomizeDialog:: RenameCategory

在 [**命令**] 頁面上, 重新命名類別清單方塊中的類別。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>參數

*lpszCategoryOld*<br/>
在要變更的類別目錄名稱。

*lpszCategoryNew*<br/>
在新的分類名稱。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

類別名稱必須是唯一的。

##  <a name="replacebutton"></a>CMFCToolBarsCustomizeDialog:: ReplaceButton

取代 [**命令**] 頁面上命令清單方塊中的工具列按鈕。

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在指定要取代之按鈕的命令。

*button*<br/>
在取代舊按鈕之工具列按鈕物件的**const**參考。

### <a name="remarks"></a>備註

當[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu)、 [CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)或[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)將命令新增至 [**命令**] 頁面時, 該命令的格式[為CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件 (或包含所`AddMenuCommands`新增子功能表之功能表項目的[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件)。 此架構也會呼叫這三種方法來自動新增命令。 如果您想要改由衍生類型來表示命令, 請呼叫`ReplaceButton`並傳入衍生類型的按鈕。

### <a name="example"></a>範例

下列範例示範如何`ReplaceButton` `CMFCToolBarsCustomizeDialog`在類別中使用方法。 此程式碼片段是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog:: SetUserCategory

在 [**命令**] 頁面上, 指定類別清單中的哪個類別為使用者類別目錄。 呼叫[CMFCToolBarsCustomizeDialog:: Create](#create)之前, 您必須先呼叫此函式。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>參數

*lpszCategory*<br/>
在類別目錄的名稱。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

架構目前未使用使用者類別設定。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)

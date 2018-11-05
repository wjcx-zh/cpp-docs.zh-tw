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
ms.openlocfilehash: 026c7392c3eb93b37a712059939683e3e0ab852c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628991"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 類別

非強制回應對話方塊 ( [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md))，可讓使用者自訂工具列、 功能表、 鍵盤快速鍵、 使用者定義的工具和應用程式中的視覺化樣式。 使用者通常會選取 [ **工具** ] 功能表中的 [ **自訂** ]，以存取這個對話方塊。

**自訂** 對話方塊中有六個索引標籤：**命令**，**工具列**，**工具**，**鍵盤**， **功能表**，並**選項**。

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
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|插入的命令清單中的工具列按鈕，在**命令**頁面|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|載入功能表資源和呼叫[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上的命令清單，以新增該功能表**命令**頁面。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|載入功能表資源和呼叫[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上的命令清單，以新增該功能表**命令**頁面。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|從資源載入工具列。 然後，針對每個命令中，功能表會呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法來插入命令的清單中的按鈕上**命令**指定分類下的頁面。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|顯示**自訂** 對話方塊。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|啟用或停用使用建立新的工具列**自訂** 對話方塊。|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|填入所提供`CListBox`物件中的命令**所有命令**類別目錄。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|填入所提供`CComboBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|填入所提供`CListBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|擷取與指定的命令識別碼相關聯的名稱|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|擷取所提供清單中有指定的文字標籤的項目數目。|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|擷取一組旗標會影響 [] 對話方塊中的行為。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|啟動影像編輯器，讓使用者可以自訂工具列按鈕或功能表項目圖示。|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|覆寫以擴大屬性工作表初始化。 (覆寫[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|終結視窗後，由架構呼叫。 (覆寫 `CPropertySheet::PostNcDestroy`。)|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|從指定的分類，或所有類別目錄中移除具有指定的命令 ID 的按鈕。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|將類別目錄的清單方塊中的類別上重新命名**命令** 索引標籤。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|在取代的命令清單中的按鈕**命令**與新的工具列按鈕物件的索引標籤。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|將分類加入至類別，將會顯示在清單中**命令** 索引標籤。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|由架構呼叫以判斷是否為有效的使用者定義的工具清單。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|使用者定義的工具的屬性變更時由架構呼叫。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|判斷是否可以指定的鍵盤快速鍵指派給某個動作。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|判斷是否可以變更使用者定義的工具。|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|由架構呼叫，當使用者選擇**工具**要求 索引標籤。|

## <a name="remarks"></a>備註

若要顯示**自訂**對話方塊方塊中，建立`CMFCToolBarsCustomizeDialog`物件，然後呼叫[CMFCToolBarsCustomizeDialog::Create](#create)方法。

雖然**自訂**對話方塊之後，應用程式運作，以限制使用者的自訂工作的特殊模式。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarsCustomizeDialog` 類別中使用各種方法。 此範例示範如何將命令的清單方塊中的工具列按鈕上**命令**頁面上，讓您藉由建立新的工具列**自訂** 對話方塊中，並顯示**自訂** 對話方塊。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。

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

插入的命令清單中的工具列按鈕，在**命令**頁面。

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
[in]指定要插入的按鈕的類別目錄識別碼。

*按鈕*<br/>
[in]指定要插入的按鈕。

*iInsertBefore*<br/>
[in]指定以零為起始的索引之前插入按鈕的工具列按鈕。

*lpszCategory*<br/>
[in]指定要插入按鈕的類別目錄字串。

### <a name="remarks"></a>備註

`AddButton`方法會忽略有標準命令 Id （例如 ID_FILE_MRU_FILE1) 按鈕，不允許的命令 (請參閱 < [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) 和虛擬按鈕。

這個方法會建立新的物件相同型別的`button`(通常[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)) 使用按鈕的執行階段類別。 然後它會呼叫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)複製的資料成員的按鈕，並將複本插入到指定的分類。

當插入新的按鈕時，它會接收`OnAddToCustomizePage`通知。

如果`iInsertBefore`為-1，按鈕會附加到類別目錄的清單; 否則它會插入具有指定索引的項目之前。

### <a name="example"></a>範例

下列範例示範如何使用`AddButton`方法的`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是一部分[滑桿範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

載入功能表資源和呼叫[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)上的命令清單，以新增該功能表**命令**頁面。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuResId*<br/>
[in]指定要載入功能表資源識別碼。

### <a name="return-value"></a>傳回值

如果功能表已順利新增，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

在呼叫`AddMenuCommands`， *bPopup*為 FALSE。 如此一來，該方法不會新增包含的命令清單的子功能表的功能表項目。 這個方法會加入的功能表項目在子功能表中的命令清單。

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

將項目加入至清單中的命令**命令**頁，以代表指定的功能表中的所有項目。

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
[in]要加入的 CMenu 物件指標。

*bPopup*<br/>
[in]指定是否要插入的快顯功能表項目清單的命令。

*lpszCategory*<br/>
[in]要插入的功能表的類別目錄名稱。

*lpszMenuPath*<br/>
[in]當命令所示，加入至名稱的前置詞**所有類別目錄**清單。

### <a name="remarks"></a>備註

`AddMenuCommands`的所有功能表項目的方法迴圈*pMenu*。 每個功能表項目不包含子功能表，這個方法會建立[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件並呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法，以將功能表項目新增為工具列按鈕的命令清單**命令**頁面。 分隔符號會忽略在此程序。

如果*bPopup*為 TRUE 時，這個方法所建立的每個含有子功能表的功能表項目[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件，並將其插入至命令的清單中，藉由呼叫`AddButton`。 否則包含子功能表的功能表項目不會顯示在清單中的命令。 在任一情況下，當`AddMenuCommands`遇到的功能表項目具有子功能表它會呼叫本身以遞迴方式，將指標傳遞至做為子功能表*pMenu*參數，並附加至的子功能表標籤*lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

從資源載入工具列。 然後，針對每個命令中，功能表會呼叫[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法來插入命令的清單中的按鈕上**命令**指定分類下的頁面。

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
[in]指定類別目錄的資源識別碼，加入至工具列。

*uiToolbarResId*<br/>
[in]指定的資源識別碼的工具列，其命令插入命令的清單。

*lpszCategory*<br/>
[in]指定要加入工具列，類別目錄的名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="example"></a>範例

下列範例示範如何使用`AddToolBar`方法中的`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是 [WordPad 範例](../../visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>備註

用來代表每個命令的控制項[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件。 新增工具列之後，您可以藉由呼叫與衍生型別的控制項取代按鈕[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)。

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

驗證的使用者工具清單的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>參數

*lstTools*<br/>
[in]使用者定義的工具，來檢查清單。

### <a name="return-value"></a>傳回值

如果使用者定義的工具清單無效，則為 true，則傳回否則為 FALSE。 預設實作永遠傳回 TRUE。

### <a name="remarks"></a>備註

架構會呼叫這個方法，以確認這些物件表示使用者定義的工具所傳回的有效性[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)。

覆寫`CheckToolsValidity`從衍生類別中的方法`CMFCToolBarsCustomizeDialog`如果您想要驗證的使用者工具，才能在使用者關閉對話方塊。 如果此方法會傳回 FALSE，當使用者按一下其中一個**關閉** 對話方塊或  按鈕的右上角的按鈕**關閉**對話方塊中，對話方塊右下角會顯示**工具**而不是關閉的索引標籤。 如果此方法會傳回 FALSE，當使用者按一下索引標籤，以離開**工具**索引標籤上，瀏覽不會發生。 您應該會顯示適當的訊息方塊，以通知使用者已造成驗證失敗的問題。

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

*pWndParentFrame*<br/>
[in]父框架指標。 這個參數必須不是 NULL。

*bAutoSetFromMenus*<br/>
[in]布林值，指定是否要從所有的功能表加入功能表命令的命令清單上**命令**頁面。 如果此參數為 TRUE，則會加入功能表命令。 否則，不會加入功能表命令。

*uiFlags*<br/>
[in]影響行為的對話方塊中的旗標的組合。 這個參數可以是下列一或多個下列值：

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in]清單的指標`CRuntimeClass`指定額外的自訂頁面的物件。

### <a name="remarks"></a>備註

*PlistCustomPages*參數的清單會參考`CRuntimeClass`指定額外的自訂頁面的物件。 建構函式使用的對話方塊中新增更多的分頁[CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法。 請參閱 CustomPages 範例的範例，加入更多的頁面**自訂** 對話方塊。

如需詳細資訊，您可以傳入之值的相關*uiFlags*參數，請參閱[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是一部分[自訂頁面範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

顯示**自訂** 對話方塊。

```
virtual BOOL Create();
```

### <a name="return-value"></a>傳回值

如果成功，建立自訂的屬性工作表，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

呼叫`Create`才是您完全初始化類別的方法。

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

啟用或停用使用建立新的工具列**自訂** 對話方塊。

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]若要啟用的使用者定義的工具列，則為 TRUE若要停用工具列，則為 FALSE。

### <a name="remarks"></a>備註

如果*bEnable*為 TRUE 時，**新增**，**重新命名**並**刪除**按鈕會顯示在**工具列**頁面。

根據預設，或如果*bEnable*是 FALSE，不會顯示這些按鈕的使用者無法定義新的工具列。

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

填入所提供`CListBox`物件中的命令**所有命令**類別目錄。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>參數

*wndListOfCommands*<br/>
[out]參考`CListBox`來填入的物件。

### <a name="remarks"></a>備註

**所有命令**類別目錄包含的所有類別目錄的命令。 [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法會將命令所提供的按鈕，以關聯**所有命令**為您的類別。

這個方法會清除所提供的內容`CListBox`之前填入中的命令物件**所有命令**類別目錄。

`CMFCMousePropertyPage`類別會使用這個方法來填入按兩下事件 清單方塊。

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

填入所提供`CComboBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
[out]參考`CComboBox`來填入的物件。

*bAddEmpty*<br/>
[in]布林值，指定是否要將類別新增至下拉式方塊，並沒有命令。 如果此參數為 TRUE，空的類別會新增至下拉式方塊中。 否則，不會新增空的類別。

### <a name="remarks"></a>備註

這個方法就像是[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)方法，但此方法適用於有`CComboBox`物件。

這個方法不會清除的內容`CComboBox`之前填入它的物件。 它可確保**所有命令**類別是下拉式方塊中的最後一個項目。

您可以使用，以新增新的命令類別[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 您可以使用，以變更現有類別的名稱[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。

`CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`類別會使用這個方法來分類鍵盤對應。

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

填入所提供`CListBox`物件中每個命令類別目錄的名稱取代**自訂** 對話方塊。

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wndCategory*<br/>
[out]參考`CListBox`來填入的物件。

*bAddEmpty*<br/>
[in]布林值，指定是否要將類別新增至清單方塊，並沒有命令。 如果此參數為 TRUE，空的類別會新增至清單方塊中。 否則，不會新增空的類別。

### <a name="remarks"></a>備註

這個方法就像是[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)方法，但此方法適用於有`CListBox`物件。

這個方法不會清除的內容`CListBox`之前填入它的物件。 它可確保**所有命令**類別是在清單方塊中的最後一個項目。

您可以使用，以新增新的命令類別[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)方法。 您可以使用，以變更現有類別的名稱[CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)方法。

`CMFCToolBarsCommandsPropertyPage`類別會使用這個方法，以顯示與每個命令類別目錄相關聯的命令清單。

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

擷取與指定的命令識別碼相關聯的名稱

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]若要擷取命令的識別碼。

### <a name="return-value"></a>傳回值

如果命令沒有與指定的命令識別碼或 NULL 相關聯的名稱。

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

擷取所提供清單中有指定的文字標籤的項目數目。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
[in]要比對的文字標籤。

*lstCommands*<br/>
[in]參考清單，其中包含`CMFCToolBarButton`物件。

### <a name="return-value"></a>傳回值

所提供的項目數清單的文字標籤 equals *lpszItemName*。

### <a name="remarks"></a>備註

提供的物件清單中的每個項目必須是型別`CMFCToolBarButton`。 這個方法會比較*lpszItemName*具有[CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)資料成員。

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

擷取一組旗標會影響 [] 對話方塊中的行為。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>傳回值

影響行為的對話方塊中的旗標集。

### <a name="remarks"></a>備註

這個方法會擷取的值*uiFlags*傳遞至建構函式的參數。 傳回值可以是下列一或多個下列值：

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|可讓使用者指定功能表的陰影外觀。  |
|AFX_CUSTOMIZE_TEXT_LABELS|可讓使用者能夠指定是否顯示文字標籤的工具列按鈕影像的下方。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|可讓使用者指定的功能表動畫樣式。  |
|AFX_CUSTOMIZE_NOHELP|移除 [自訂] 對話方塊中的 [說明] 按鈕。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|可讓 WS_EX_CONTEXTHELP 視覺化樣式。  |
|AFX_CUSTOMIZE_NOTOOLS|移除**工具**從自訂對話方塊的頁面。 這個旗標是否有效，如果您的應用程式使用`CUserToolsManager`類別。  |
|AFX_CUSTOMIZE_MENUAMPERS|可讓按鈕標題包含連字號 ( **&**) 字元。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|移除**大圖示**從自訂對話方塊中的選項。  |

如需有關 WS_EX_CONTEXTHELP 視覺化樣式的詳細資訊，請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

只有在發生後立即回應的使用者工具中的變更。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in、 out]已變更的使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者變更使用者定義的工具的屬性，這個方法是由架構呼叫。 預設實作不做任何動作。 衍生自的類別中置換此方法`CMFCToolBarsCustomizeDialog`執行處理的使用者工具的變更發生之後。

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

因為使用者定義它們，請驗證鍵盤快速鍵。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>參數

*pAccel*<br/>
[in、 out]指標會以建議的鍵盤指派[加速度](/windows/desktop/api/winuser/ns-winuser-tagaccel)結構。

### <a name="return-value"></a>傳回值

如果索引鍵可以是已指派或 FALSE，如果您無法指定索引鍵，則為 TRUE。 預設實作永遠傳回 TRUE。

### <a name="remarks"></a>備註

覆寫此方法，執行額外處理，當使用者指派新的鍵盤快速鍵，或要驗證使用者的鍵盤快速鍵它們定義在衍生類別中。 若要避免指派捷徑，傳回 FALSE。 您應該也會顯示訊息方塊或否則通知使用者已拒絕的鍵盤快速鍵的原因的原因。

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

執行自訂的處理時的使用者工具變更使用者將要套用變更時。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[in、 out]即將被取代的使用者工具物件的指標。

### <a name="remarks"></a>備註

變更使用者定義的工具的屬性時，這個方法是由架構呼叫。 預設實作不做任何動作。 覆寫`OnBeforeChangeTool`之類別中衍生自`CMFCToolBarsCustomizeDialog`如果您想要執行處理的使用者工具的變更發生，例如釋放資源之前， *pSelTool*使用。

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

啟動影像編輯器，讓使用者可以自訂工具列按鈕或功能表項目圖示。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]父視窗的指標。

*點陣圖*<br/>
[in]若要編輯點陣圖物件的參考。

*nBitsPerPixel*<br/>
[in]點陣圖的色彩解析度，以位元 / 像素。

### <a name="return-value"></a>傳回值

如果正在認可變更，則為 TRUE否則為 FALSE。 預設實作會顯示一個對話方塊，則傳回 TRUE，如果使用者按一下**確定**，或 FALSE，如果使用者按一下**取消**或**關閉** 按鈕。

### <a name="remarks"></a>備註

使用者執行影像編輯器時，這個方法是由架構呼叫。 預設實作會顯示[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md) 對話方塊。 覆寫`OnEditToolbarMenuImage`衍生類別中使用自訂映像編輯器中。

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

覆寫以擴大屬性工作表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

呼叫的結果[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作中， [cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)，藉由顯示**關閉** 按鈕，藉由確認對話方塊中，以符合目前的螢幕大小，並藉由移動**協助**對話方塊的左下角的按鈕。

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

處理從 framework 通知所**工具**頁面即將進行初始化。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>備註

預設實作不做任何動作。 覆寫此方法來處理此通知在衍生類別中。

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

終結視窗後，由架構呼叫。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>備註

此方法擴充的基底類別實作， `CPropertySheet::PostNcDestroy`，藉由還原為上一個模式的應用程式。

[CMFCToolBarsCustomizeDialog::Create](#create)方法會將應用程式放在限制使用者的自訂工作的特殊模式。

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

從指定的分類，或所有類別目錄中移除具有指定的命令 ID 的按鈕。

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
[in]指定要從中移除 按鈕的類別目錄識別碼。

*uiCmdId*<br/>
[in]指定按鈕的命令識別碼。

*lpszCategory*<br/>
[in]指定要從中移除 按鈕的類別目錄的名稱。

### <a name="return-value"></a>傳回值

[移除] 按鈕，則為-1 指定的類別目錄中找不到指定的命令 ID 的以零為起始的索引。 如果*uiCategoryId*為-1，傳回的值為 0。

### <a name="remarks"></a>備註

若要移除所有類別目錄中的按鈕，呼叫此方法和集合的第一個多載*uiCategoryId*為-1。

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

將類別目錄的清單方塊中的類別上重新命名**命令**頁面。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>參數

*lpszCategoryOld*<br/>
[in]若要變更類別名稱。

*lpszCategoryNew*<br/>
[in]新的類別名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

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

*uiCmd*<br/>
[in]指定按鈕的命令，來取代。

*按鈕*<br/>
[in]A **const**取代舊的按鈕的工具列按鈕物件的參考。

### <a name="remarks"></a>備註

當[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)， [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)，或[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)新增命令**命令**頁面上，命令會採用[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件 (或[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)功能表的物件包含新增的子功能表項目`AddMenuCommands`)。 架構也會呼叫這三種方法，會自動新增的命令。 如果您想要改為以衍生類型的命令時，呼叫`ReplaceButton`並傳入衍生類型的按鈕。

### <a name="example"></a>範例

下列範例示範如何使用`ReplaceButton`方法中的`CMFCToolBarsCustomizeDialog`類別。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

指定哪個類別清單中的類別上**命令**頁面是使用者類別。 您必須呼叫此函式，然後再呼叫[CMFCToolBarsCustomizeDialog::Create](#create)。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>參數

*lpszCategory*<br/>
[in]類別目錄的名稱。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

Framework 目前不使用使用者分類設定。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)

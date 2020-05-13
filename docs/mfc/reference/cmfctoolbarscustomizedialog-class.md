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
ms.openlocfilehash: 29e2c3d0238ac5a084ea916d95ad953f8c4aedce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753410"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog 類別

一個無模式選項卡對話框 ( [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)), 使用戶能夠自訂應用程式中的工具列、功能表、鍵盤快捷鍵、使用者定義的工具和視覺樣式。 使用者通常會選取 [ **工具** ] 功能表中的 [ **自訂** ]，以存取這個對話方塊。

**「自訂」** 對話框有六個選項卡:**命令**,**工具列, 工具、****鍵盤**、**選單**與**選項**。**Keyboard**

## <a name="syntax"></a>語法

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC工具列自訂對話框::CMFC工具列自定義對話框](#cmfctoolbarscustomizedialog)|建構 `CMFCToolBarsCustomizeDialog` 物件。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC工具列自訂對話::添加按鈕](#addbutton)|將工具列按鈕插入**命令頁上的指令**清單中|
|[CMFC工具列自訂對話::新增選單](#addmenu)|從資源載入選單並調用[CMFCToolBars 自訂對話框:添加Menu命令](#addmenucommands)以將該選單添加到**命令**頁面上的命令清單中。|
|[CMFC工具列自訂對話::新增選單命令](#addmenucommands)|從資源載入選單並調用[CMFCToolBars 自訂對話框:添加Menu命令](#addmenucommands)以將該選單添加到**命令**頁面上的命令清單中。|
|[CMFC工具列自訂對話框::添加工具列](#addtoolbar)|從資源載入工具列。 然後,對於菜單中的每個命令,調用[CMFCToolBars自定義對話框::AddButton](#addbutton)方法,在指定類別下**的命令**頁上的命令列表中插入一個按鈕。|
|[CMFC工具列自訂對話::建立](#create)|顯示 **「自訂」** 對話方塊。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|保留供未來使用。|
|[CMFC工具列自訂對話框::啟用使用者定義的工具列](#enableuserdefinedtoolbars)|使用 **「自訂」** 對話框啟用或關閉新的工具列。|
|[CMFC工具列自訂對話框::填充所有命令清單](#fillallcommandslist)|使用`CListBox`**「所有命令」** 類別中的命令填充提供的物件。|
|[CMFC工具列自訂對話::填充類別組合框](#fillcategoriescombobox)|使用`CComboBox`**「自訂」** 對話方塊中每個指令類別的名稱填充提供的物件。|
|[CMFC工具列自訂對話框::填充類別清單框](#fillcategorieslistbox)|使用`CListBox`**「自訂」** 對話方塊中每個指令類別的名稱填充提供的物件。|
|[CMFC工具列自訂對話框::取得命令名稱](#getcommandname)|檢索與給定命令 ID 關聯的名稱。|
|[CMFC工具列自訂對話::取得計數類別](#getcountincategory)|檢索提供清單中具有給定文本標籤的項數。|
|[CMFC工具列自訂對話::獲取 Flags](#getflags)|檢索影響對話框行為的標誌集。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC工具列自訂對話框::編輯工具列選單影像](#onedittoolbarmenuimage)|啟動圖像編輯器,以便用戶可以自定義工具列按鈕或功能表示。|
|[CMFC工具列自訂對話::oninitDialog](#oninitdialog)|用於增強屬性表初始化的重寫。 (覆寫[C 屬性表:oninitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFC工具列自定義對話::Postnc銷毀](#postncdestroy)|視窗被破壞後由框架調用。 (覆寫 `CPropertySheet::PostNcDestroy`。)|
|[CMFC工具列自訂對話::刪除按鈕](#removebutton)|從指定類別或所有類別中刪除具有指定命令 ID 的按鈕。|
|[CMFC工具列自訂對話框:重新命名類別](#renamecategory)|在 **「命令」** 選項卡上的類別清單框中重新命名類別。|
|[CMFC工具列自訂對話::取代按鈕](#replacebutton)|將 **「命令」** 選項卡上命令清單中的按鈕取代為新的工具列按鈕物件。|
|[CMFC工具列自訂對話框::設定使用者類別](#setusercategory)|將類別添加到將顯示在 **「命令」** 選項卡上的類別清單中。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC工具列自訂對話::檢查工具有效性](#checktoolsvalidity)|由框架呼叫以確定使用者定義的工具清單是否有效。|
|[CMFC工具列自訂對話框::在更改工具後開啟](#onafterchangetool)|當使用者定義的工具的屬性發生更改時,由框架調用。|
|[CMFC工具列自定義對話::在分配鍵上](#onassignkey)|確定是否可以將指定的鍵盤快捷方式分配給操作。|
|[CMFC工具列自訂對話::在更改工具之前開啟](#onbeforechangetool)|確定是否可以更改使用者定義的工具。|
|[CMFC工具列自訂對話::oninitToolspage](#oninittoolspage)|當使用者選擇「**工具**」選項卡時,框架呼叫。|

## <a name="remarks"></a>備註

要顯示 **「自訂」** 對話方塊`CMFCToolBarsCustomizeDialog`,請建立一個物件並調用[CMFCToolBars 自訂對話框::建立](#create)方法。

當 **「自訂」** 對話框處於活動狀態時,應用程式以特殊模式工作,該模式將使用者限制為自訂任務。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarsCustomizeDialog` 類別中使用各種方法。 該範例展示如何在 **「命令」** 頁上的命令列表框中取代工具列按鈕,使用 **「自訂」** 對話框啟用創建新工具列,以及顯示 **「自訂」** 對話方塊。 此代碼段是[IE 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>需求

**標題:** afxToolBars自定義對話.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFC工具列自訂對話::添加按鈕

將工具列按鈕插入到 **「命令」** 頁上的命令清單中。

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

*UI 分類代碼*<br/>
[在]指定要插入按鈕的類別 ID。

*按鈕*<br/>
[在]指定要插入的按鈕。

*iInsert 之前*<br/>
[在]指定工具列按鈕的零索引,在插入按鈕之前。

*lpsz 類別*<br/>
[在]指定要插入按鈕的類別字串。

### <a name="remarks"></a>備註

該方法`AddButton`忽略具有標準命令 ID(如ID_FILE_MRU_FILE1)、不允許的命令(請參閱[CMFCToolBar::IsCommand 允許](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted))和虛擬按鈕的按鈕。

此方法通過使用按鈕的運行時類創建與`button`(通常[CMFCToolBarButton 類](../../mfc/reference/cmfctoolbarbutton-class.md)) 類型相同的新物件。 然後調用[CMFCToolBarButton::從複製](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)以複製按鈕的數據成員,並將副本插入到指定的類別中。

插入新按鈕時,它將收到`OnAddToCustomizePage`通知。

如果`iInsertBefore`為 -1,則該按鈕將追加到類別清單中;如果為 -1,則該按鈕將追加到類別清單中。否則,它將插入具有指定索引的項之前。

### <a name="example"></a>範例

下面的示例演示如何使用`AddButton``CMFCToolBarsCustomizeDialog`類的方法。 此代碼段是[滑塊示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFC工具列自訂對話::新增選單

從資源載入選單並調用[CMFCToolBars 自訂對話框:添加Menu命令](#addmenucommands)以將該選單添加到**命令**頁面上的命令清單中。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>參數

*uiMenuResId*<br/>
[在]指定要載入的選單的資源 ID。

### <a name="return-value"></a>傳回值

如果已成功添加功能表,則為 TRUE;如果功能表已成功添加,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

在調用`AddMenuCommands`中 *,bPopup*是 FALSE。 因此,該方法不會將包含子菜單的功能表項添加到命令清單中。 此方法會將子選單中的功能表項添加到命令清單中。

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFC工具列自訂對話::新增選單命令

將項添加到 **「命令」** 頁中的命令清單中,以表示指定選單中的所有項。

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
[在]指向要添加的 CMenu 物件的指標。

*bPopup*<br/>
[在]指定是否將彈出選單項插入到命令清單中。

*lpsz 類別*<br/>
[在]要插入功能表的類別的名稱。

*lpszMenuPath*<br/>
[在]當命令顯示在 **「所有類別」** 清單中時添加到名稱的前置碼。

### <a name="remarks"></a>備註

該方法`AddMenuCommands`迴圈訪問*pMenu*的所有功能表項。 對於不包含子選單的每個選單項,此方法將創建一個[CMFCToolBarButton 類](../../mfc/reference/cmfctoolbarbutton-class.md)物件,並調用[CMFCToolBar 自定義對話框::AddButton](#addbutton)方法,將功能表項作為工具列按鈕添加到**命令**頁上的命令列表中。 在此過程中將忽略分隔符。

如果*bPopup*為 TRUE,則對於包含子選單的每個選單項,此方法創建一個[CMFCToolBarMenuButton 類](../../mfc/reference/cmfctoolbarmenubutton-class.md)`AddButton`物件,並透過調用 將其插入到命令清單中。 否則,包含子功能表的功能表項不會顯示在命令清單中。 在這兩種情況下,當`AddMenuCommands`遇到選單項與子選單時,它調用自身遞迴,將指向子選單的指標作為*pMenu*參數傳遞,並將子選單的標籤追加到*lpszMenuPath*。

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFC工具列自訂對話框::添加工具列

從資源載入工具列。 然後,對於菜單中的每個命令,調用[CMFCToolBars自定義對話框::AddButton](#addbutton)方法,在指定類別下**的命令**頁上的命令列表中插入一個按鈕。

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>參數

*UI 分類代碼*<br/>
[在]指定要向其添加工具列的類別的資源 ID。

*uiToolbarResId*<br/>
[在]指定其指令插入到命令清單中的工具列的資源識別碼。

*lpsz 類別*<br/>
[在]指定要向其添加工具列的類別的名稱。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="example"></a>範例

下面的示例演示如何在`AddToolBar``CMFCToolBarsCustomizeDialog`類中使用 方法。 此程式碼片段是 [WordPad 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>備註

用於表示每個命令的控制項是[CMFCToolBarButton 類](../../mfc/reference/cmfctoolbarbutton-class.md)物件。 添加工具列后,可以通過調用[CMFCToolBars自定義對話方塊:::替換按鈕](#replacebutton),將按鈕替換為派生類型的控制項。

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFC工具列自訂對話::檢查工具有效性

驗證使用者工具清單的有效性。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>參數

*lstTools*<br/>
[在]要檢查的使用者定義工具的清單。

### <a name="return-value"></a>傳回值

如果使用者定義的工具清單有效,則返回 TRUE;否則 FALSE。 預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

框架呼叫此方法來驗證表示[CMFCToolBars 自訂對話框](#checktoolsvalidity)傳回的使用者定義工具的物件的有效性::檢查工具有效性 。

如果要在`CheckToolsValidity`使用者關閉對話方塊之前驗證`CMFCToolBarsCustomizeDialog`使用者工具,請覆蓋派生的類中的方法。 如果使用者按下對話框右上角的 **「關閉**」按鈕或對話框右下角標記為「**關閉**」的按鈕時,此方法將返回 FALSE,則該對話框將顯示 **「工具**」選項卡,而不是關閉。 如果用戶按下選項卡以從 **「工具」** 選項卡導航時返回 FALSE,則不會發生導航。 應顯示一個適當的消息框,以通知用戶導致驗證失敗的問題。

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFC工具列自訂對話框::CMFC工具列自定義對話框

建構 `CMFCToolBarsCustomizeDialog` 物件。

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>參數

*pwnd 父架構*<br/>
[在]指向父幀的指標。 此參數不能為 NULL。

*b 自動從選單中設定*<br/>
[在]布林值,用於指定是否將所有選單中的功能表命令添加到 **「命令」** 頁上的命令清單中。 如果此參數為 TRUE,則添加功能表命令。 否則,將不會添加功能表命令。

*uiFlags*<br/>
[在]影響對話框行為的標誌的組合。 這裡可以是以下一個或多個值:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plist 自訂頁面*<br/>
[在]指向指定其他自定義頁的物件`CRuntimeClass`列表的指標。

### <a name="remarks"></a>備註

*plistCustomPages*參數是指指定其他自定義`CRuntimeClass`頁面 的物件清單。 建構函數使用[CRuntimeClass::createObject](../../mfc/reference/cruntimeclass-structure.md#createobject)方法向對話方塊添加更多頁面。 有關向 **「自定義」** 對話方塊添加更多頁面的範例,請參閱自訂頁面範例。

有關可以在*uiFlags*參數中傳遞的值的詳細資訊,請參閱[CMFCToolBars 自訂對話框::getFlags](#getflags)。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCToolBarsCustomizeDialog`類的物件。 此代碼段是[自定義頁示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFC工具列自訂對話::建立

顯示 **「自訂」** 對話方塊。

```
virtual BOOL Create();
```

### <a name="return-value"></a>傳回值

如果自定義屬性表已成功創建,則為 TRUE;如果自定義屬性表已成功創建,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

僅在完全`Create`初始化類后調用 方法。

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFC工具列自訂對話框::啟用使用者定義的工具列

使用 **「自訂」** 對話框啟用或關閉新的工具列。

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 啟用使用者定義的工具列;FALSE 以禁用工具列。

### <a name="remarks"></a>備註

如果*啟用*為 TRUE,則**New**「新建 **」重新命名**和**刪除**按鈕會顯示在**工具列**頁上。

預設情況下,或者如果*bEnable*是 FALSE,則不顯示這些按鈕,並且使用者無法定義新的工具列。

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFC工具列自訂對話框::填充所有命令清單

使用`CListBox`**「所有命令」** 類別中的命令填充提供的物件。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>參數

*wndList命令*<br/>
[出]對要填充的物件`CListBox`的引用。

### <a name="remarks"></a>備註

「**所有命令」** 類別包含所有類別的命令。 [CMFCToolBars自定義對話框:AddButton](#addbutton)方法將與您提供的按鈕關聯的命令添加到 **「所有命令」** 類別。

此方法清除提供`CListBox`的物件的內容,然後再使用 **「所有命令」** 類別中的命令填充它。

類別`CMFCMousePropertyPage`使用此方法填充按兩下事件清單框。

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFC工具列自訂對話::填充類別組合框

使用`CComboBox`**「自訂」** 對話方塊中每個指令類別的名稱填充提供的物件。

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wnd分類*<br/>
[出]對要填充的物件`CComboBox`的引用。

*bAddEmpty*<br/>
[在]指定是否向沒有命令的組合框添加類別的布林值。 如果此參數為 TRUE,則空類別將添加到組合框中。 否則,不會添加空類別。

### <a name="remarks"></a>備註

此方法類似於[CMFCToolBars 自定義對話框::填充類別清單框](#fillcategorieslistbox)方法,但`CComboBox`此方法適用於 物件。

此方法在填充`CComboBox`物件之前不會清除物件的內容。 它保證 **「所有命令」** 類別是組合框中的最後一項。

您可以使用[CMFCToolBars 自訂對話框::addButton](#addbutton)方法添加新的命令類別。 您可以使用[CMFCToolBars 自定義對話框::重新命名類別](#renamecategory)方法更改現有類別的名稱。

`CMFCToolBarsKeyboardPropertyPage`和`CMFCKeyMapDialog`類使用此方法對鍵盤映射進行分類。

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFC工具列自訂對話框::填充類別清單框

使用`CListBox`**「自訂」** 對話方塊中每個指令類別的名稱填充提供的物件。

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>參數

*wnd分類*<br/>
[出]對要填充的物件`CListBox`的引用。

*bAddEmpty*<br/>
[在]指定是否將類別加入在命令的清單盒中的布林值。 如果此參數為 TRUE,則空類別將添加到列表框中。 否則,不會添加空類別。

### <a name="remarks"></a>備註

此方法類似於[CMFCToolBars 自定義對話框::填充類別ComboBox](#fillcategoriescombobox)方法,但`CListBox`此方法適用於 物件。

此方法在填充`CListBox`物件之前不會清除物件的內容。 它保證 **「所有命令」** 類別是清單框中的最後一項。

您可以使用[CMFCToolBars 自訂對話框::addButton](#addbutton)方法添加新的命令類別。 您可以使用[CMFCToolBars 自定義對話框::重新命名類別](#renamecategory)方法更改現有類別的名稱。

類別`CMFCToolBarsCommandsPropertyPage`使用此方法顯示與每個指令類別關聯的命令清單。

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFC工具列自訂對話框::取得命令名稱

檢索與給定命令 ID 關聯的名稱。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]要檢索的命令的 ID。

### <a name="return-value"></a>傳回值

與給定命令 ID 關聯的名稱,如果命令不存在,則為 NULL。

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFC工具列自訂對話::取得計數類別

檢索提供清單中具有給定文本標籤的項數。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>參數

*lpszItem名稱*<br/>
[在]要匹配的文本標籤。

*lstCommands*<br/>
[在]對包含物件的清單的`CMFCToolBarButton`引用。

### <a name="return-value"></a>傳回值

提供清單中的文字標籤等於*lpszItemName*的項目數。

### <a name="remarks"></a>備註

提供的物件清單中的每個元素必須為類型`CMFCToolBarButton`。 此方法將*lpszItemName*與[CMFCToolBarButton:::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)數據成員進行比較。

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFC工具列自訂對話::獲取 Flags

檢索影響對話框行為的標誌集。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>傳回值

影響對話框行為的標誌集。

### <a name="remarks"></a>備註

此方法檢索傳遞給建構函數的*uiFlags*參數的值。 傳回值可以是以下一個或多個值:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|允許使用者指定功能表的捲影外觀。  |
|AFX_CUSTOMIZE_TEXT_LABELS|允許使用者指定文本標籤是否顯示在工具列按鈕圖像下方。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|允許使用者指定功能表動畫樣式。  |
|AFX_CUSTOMIZE_NOHELP|從自定義對話框中刪除説明按鈕。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|啟用WS_EX_CONTEXTHELP視覺樣式。  |
|AFX_CUSTOMIZE_NOTOOLS|從自訂對話框中移除 **「工具」** 頁。 如果應用程式使用類,`CUserToolsManager`則此標誌有效。  |
|AFX_CUSTOMIZE_MENUAMPERS|允許按鈕標題包含安培和**&**( ) 字元。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|從自訂對話框中刪除 **「大圖示**」選項。  |

有關WS_EX_CONTEXTHELP視覺樣式的詳細資訊,請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)。

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFC工具列自訂對話框::在更改工具後開啟

在使用者工具發生後立即回應更改。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[進出]指向已更改的使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者更改使用者定義工具的屬性時,框架將調用此方法。 預設實作不做任何動作。 在派生的`CMFCToolBarsCustomizeDialog`類中重寫此方法,以便對使用者工具進行更改後執行處理。

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFC工具列自定義對話::在分配鍵上

在使用者定義鍵盤快捷方式時對其進行驗證。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>參數

*pAccel*<br/>
[進出]指向建議的鍵盤 assigment 的指標,該指標表示為[ACCEL](/windows/win32/api/winuser/ns-winuser-accel)結構。

### <a name="return-value"></a>傳回值

如果可以分配金鑰,則為 TRUE;如果無法分配密鑰,則為 FALSE。 預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

在派生類中重寫此方法,以在使用者分配新的鍵盤快捷鍵時執行額外處理,或在使用者定義鍵盤快捷方式時驗證它們。 要防止分配快捷方式,返回 FALSE。 您還應顯示消息框或以其他方式通知用戶鍵盤快捷方式被拒絕的原因。

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFC工具列自訂對話::在更改工具之前開啟

當使用者要應用更改時對使用者工具進行更改時,執行自定義處理。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>參數

*pSelTool*<br/>
[進出]指向即將替換的使用者工具物件的指標。

### <a name="remarks"></a>備註

當使用者定義工具的屬性即將更改時,框架將調用此方法。 預設實作不做任何動作。 如果要在發生`OnBeforeChangeTool`對使用者工具進行更改之前`CMFCToolBarsCustomizeDialog`執行 處理,例如釋放*pSelTool*使用的資源,請覆蓋派生的類中的方法。

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFC工具列自訂對話框::編輯工具列選單影像

啟動圖像編輯器,以便用戶可以自定義工具列按鈕或功能表示。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向父視窗的指標。

*點陣圖*<br/>
[在]對要編輯的點陣圖物件的引用。

*nBitsPerPixel*<br/>
[在]位圖顏色解析度,以每圖元位為單位。

### <a name="return-value"></a>傳回值

如果正在實施更改,則為 TRUE;否則 FALSE。 預設實現顯示一個對話框,如果使用者按下 **「確定」** 或「如果使用者按下」**取消「****關閉**」 按鈕,則傳回 TRUE。

### <a name="remarks"></a>備註

當使用者運行圖像編輯器時,框架呼叫此方法。 預設實現顯示[CMFCImage 編輯器對話類](../../mfc/reference/cmfcimageeditordialog-class.md)對話框。 在`OnEditToolbarMenuImage`派生類中重寫以使用自定義圖像編輯器。

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFC工具列自訂對話::oninitDialog

用於增強屬性表初始化的重寫。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

呼叫[CPropertySheet 的結果:onitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)方法。

### <a name="remarks"></a>備註

此方法透過顯示 **「關閉」** 按鈕、確保對話框適合當前螢幕大小以及**將 「説明」** 按鈕移動到對話框的左下角來擴展基類實現[CProperty Sheet:onInitDialog。](../../mfc/reference/cpropertysheet-class.md#oninitdialog)

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFC工具列自訂對話::oninitToolspage

處理框架中有關"**工具"** 頁即將初始化的通知。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>備註

預設實作不做任何動作。 重寫派生類中的此方法以處理此通知。

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFC工具列自定義對話::Postnc銷毀

視窗被破壞後由框架調用。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>備註

此方法通過將應用程式還原到以前的模式來`CPropertySheet::PostNcDestroy`擴展基類實現。

[CMFCToolBars自定義對話框:創建](#create)方法將應用程式置於將使用者限制為自定義任務的特殊模式。

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFC工具列自訂對話::刪除按鈕

從指定類別或所有類別中刪除具有指定命令 ID 的按鈕。

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>參數

*UI 分類代碼*<br/>
[在]指定要從中刪除按鈕的類別 ID。

*烏伊CmDId*<br/>
[在]指定按鈕的命令識別碼。

*lpsz 類別*<br/>
[在]指定要從中刪除按鈕的類別的名稱。

### <a name="return-value"></a>傳回值

刪除按鈕的零基索引,如果在指定類別中找不到指定的命令 ID,則為 -1。 如果*uiCategoryId*為 -1,則返回值為 0。

### <a name="remarks"></a>備註

要從所有類別中刪除按鈕,請調用此方法的第一個重載,並將*uiCategoryId*設置為 -1。

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFC工具列自訂對話框:重新命名類別

在 **「命令」** 頁上的類別清單框中重新命名類別。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>參數

*lpsz分類Old*<br/>
[在]要更改的類別名稱。

*lpsz 分類新*<br/>
[在]新的類別名稱。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

類別名稱必須是唯一的。

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFC工具列自訂對話::取代按鈕

在 **「命令」** 頁上的命令列表框中取代工具列按鈕。

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]指定要替換的按鈕的命令。

*按鈕*<br/>
[在]對替換舊按鈕的工具列按鈕物件的**const**引用。

### <a name="remarks"></a>備註

當[CMFCToolBars 自定義對話框::添加](#addmenu)Menu,CMFCToolBars[自定義對話方塊:](#addmenucommands)或[CMFCToolBars自定義對話框:addToolBar](#addtoolbar)向**指令**頁添加命令時,該命令以[CMFCToolBarButton 類](../../mfc/reference/cmfctoolbarbutton-class.md)物件(或包含 添加`AddMenuCommands`的子功能表的功能表項的[CMFCToolBarMenuButton 類](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件)的形式出現。 框架還調用這三種方法自動添加命令。 如果希望命令由派生類型來表示,請調用`ReplaceButton`並傳遞派生類型的按鈕。

### <a name="example"></a>範例

下面的示例演示如何在`ReplaceButton``CMFCToolBarsCustomizeDialog`類中使用 方法。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFC工具列自訂對話框::設定使用者類別

指定 **「指令」** 頁上的類別清單中的哪個類別是使用者類別。 在調用[CMFCToolBars 自定義對話框::::創建](#create)之前,必須調用此功能。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>參數

*lpsz 類別*<br/>
[在]類別的名稱。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

框架當前不使用使用者類別設置。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)

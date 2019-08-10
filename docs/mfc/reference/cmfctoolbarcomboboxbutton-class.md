---
title: CMFCToolBarComboBoxButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915974"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 類別

包含下拉式方塊控制項 ( [CComboBox 類別](../../mfc/reference/ccombobox-class.md)) 的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|建構 `CMFCToolBarComboBoxButton`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|將專案新增至下拉式方塊清單的結尾。|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|將專案新增至下拉式方塊清單。 清單中的專案順序是由`Compare`所指定。|
|[CMFCToolBarComboBoxButton::Compare](#compare)|比較兩個專案。 呼叫以排序加入下拉式`AddSortedItems`方塊清單的專案。|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|為下拉式方塊按鈕建立新的編輯控制項。|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|從下拉式方塊清單中刪除專案。|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|傳回包含指定之字串的專案索引。|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|使用指定的命令識別碼, 傳回下拉式方塊按鈕的指標。|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|傳回下拉式方塊控制項的指標, 內嵌在下拉式方塊按鈕中。|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|傳回下拉式方塊清單中的專案數。|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|尋找具有指定命令識別碼的下拉式方塊按鈕。 傳回該按鈕的下拉式方塊清單中的專案數。|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|傳回下拉式方塊清單中所選取專案的索引。|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|尋找具有指定命令識別碼的下拉式方塊按鈕, 並在該按鈕的下拉式方塊清單中傳回所選取專案的索引。|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|傳回下拉式方塊按鈕中內嵌之編輯控制項的指標。|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|傳回與下拉式方塊清單中指定之索引相關聯的字串。|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|尋找具有指定命令識別碼的下拉式方塊按鈕, 並傳回與該按鈕的下拉式方塊清單中的索引相關聯的字串。|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|傳回與下拉式方塊清單中指定索引相關聯的32位值。|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|尋找具有指定命令識別碼的下拉式方塊按鈕, 並傳回與該按鈕的下拉式方塊清單中的索引相關聯的32位值。|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|尋找具有指定命令識別碼的下拉式方塊按鈕。 在該按鈕的下拉式方塊清單中, 抓取與索引相關聯的32位值, 並傳回32位值做為指標。|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|從下拉式方塊的編輯控制項傳回文字。|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|尋找具有指定命令識別碼的下拉式方塊按鈕, 並從該按鈕的編輯控制項傳回文字。|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|決定應用程式中的下拉式方塊按鈕是否置中, 或與工具列頂端對齊。|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|決定應用程式中的下拉式方塊按鈕是否具有平面外觀。|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|從下拉式方塊的清單方塊和編輯控制項中移除所有專案。|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根據下拉式方塊中的索引、32位值或字串來選取專案, 並通知下拉式方塊控制項選取範圍。|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|尋找具有指定命令識別碼的下拉式方塊按鈕。 呼叫`SelectItem` , 以根據其字串、索引或32位值, 在該按鈕的下拉式方塊中選取專案。|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定應用程式中的下拉式方塊按鈕是以垂直方式置中或對齊工具列的頂端。|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|設定下拉式清單方塊的高度。|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定應用程式中的下拉式方塊按鈕是否具有平面外觀。|

## <a name="remarks"></a>備註

若要將下拉式方塊按鈕新增至工具列, 請依照下列步驟執行:

1. 為父工具列資源的按鈕保留假的資源 ID。

2. `CMFCToolBarComboBoxButton`建立物件。

3. 在處理 AFX_WM_RESETTOOLBAR 訊息的訊息處理常式中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton), 將虛擬按鈕取代為新的下拉式方塊按鈕。

如需詳細資訊，請參閱[逐步解說：將控制項放在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具列上。 如需下拉式列示方塊工具列按鈕的範例, 請參閱範例專案 VisualStudioDemo。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarComboBoxButton` 類別中使用各種方法。 此範例示範如何啟用編輯和下拉式方塊、設定應用程式中下拉式方塊按鈕的垂直位置、在下拉時設定清單方塊的高度、設定應用程式中下拉式方塊按鈕的平面樣式外觀。, 然後在下拉式方塊按鈕的編輯方塊中設定文字。 此程式碼片段是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>需求

**標頭:** afxtoolbarcomboboxbutton。h

##  <a name="additem"></a>CMFCToolBarComboBoxButton:: AddItem

將唯一的專案附加至清單方塊。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
在要加入清單方塊之專案的文字。

*dwData*<br/>
在與要加入清單方塊的專案相關聯的資料。

### <a name="return-value"></a>傳回值

清單方塊中最後一個專案的索引。

### <a name="remarks"></a>備註

當清單方塊樣式已排序時, 請勿使用這個方法。

如果專案文字已經在清單方塊中, 新的資料就會與現有的專案一起儲存。 專案的搜尋會區分大小寫。

##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

依照[Compare](#compare)方法所定義的順序, 將專案加入清單方塊中。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
在要加入清單方塊之專案的文字。

*dwData*<br/>
在與要加入清單方塊的專案相關聯的資料。

### <a name="return-value"></a>傳回值

已新增至清單方塊之專案的索引。

### <a name="remarks"></a>備註

使用此函式可依特定順序將專案新增至清單方塊。

##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

指出下拉式方塊按鈕的大小是否可以變更。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

傳回 TRUE。

##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

結構[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
在新按鈕的命令識別碼。

*iImage*<br/>
在與 [新增] 按鈕相關聯之影像的影像索引。

*dwStyle*<br/>
在[新增] 按鈕的樣式。

*iWidth*<br/>
在[新增] 按鈕的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

預設寬度為150圖元。

如需工具列按鈕樣式的清單, 請參閱[工具列控制項樣式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

刪除使用者定義的資料。

```
virtual void ClearData();
```

### <a name="remarks"></a>備註

根據預設, 此方法不會執行任何操作。 如果您想要刪除任何使用者定義的資料, 請在衍生類別中覆寫這個方法。

##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare

比較兩個字串。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>參數

*lpszItem1*<br/>
在要比較的第一個字串。

*lpszItem2*<br/>
在要比較的第二個字串。

### <a name="return-value"></a>傳回值

值, 指出字串之間區分大小寫的詞典編纂關聯性。 下表列出可能的值:

|值|說明|
|-----------|-----------------|
|\<0|第一個字串小於第二個。|
|0|第一個字串等於第二個。|
|>0|第一個字串大於第二個。|

### <a name="remarks"></a>備註

覆寫這個方法, 以變更清單方塊中專案的排序方式。

比較會區分大小寫。

這個方法只會從[AddSortedItem](#addsorteditem)方法呼叫。

##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton:: CopyFrom

將指定`CMFCToolBarComboBoxButton`的狀態複製到目前的物件。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
在來源`CMFCToolBarComboBoxButton`物件。

##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo

為下拉式方塊按鈕建立新的下拉式方塊。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在按鈕父視窗的指標。

*rect*<br/>
在下拉式方塊的周框。

### <a name="return-value"></a>傳回值

如果方法成功, 則為新下拉式方塊的指標;否則為 Null。

##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

為下拉式方塊按鈕建立新的編輯方塊。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在按鈕父視窗的指標。

*rect*<br/>
在新編輯方塊的周框。

*dwEditStyle*<br/>
在新編輯方塊的控制項樣式。

### <a name="return-value"></a>傳回值

如果方法成功, 則為新編輯方塊的指標;否則為 Null。

### <a name="remarks"></a>備註

當此架構為下拉式方塊按鈕建立新的編輯方塊時, 會呼叫這個方法。 覆寫此方法以變更[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)的建立方式。

##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::D eleteItem

從清單方塊中刪除指定的專案。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在要刪除的專案之以零為起始的索引。

*dwData*<br/>
在與要刪除的專案相關聯的資料。

*lpszText*<br/>
在要刪除之專案的文字。 如果有多個專案具有相同的文字, 則會刪除第一個專案。

### <a name="return-value"></a>傳回值

如果已找到專案並成功刪除, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

複製使用者定義的資料。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>備註

根據預設, 此方法不會執行任何操作。 如果您想要複製任何使用者定義的資料, 請在衍生類別中覆寫這個方法。

##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

啟用或停用編輯和下拉式方塊。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示啟用編輯和下拉式方塊;FALSE 表示停用編輯和下拉式方塊。

### <a name="remarks"></a>備註

停用時, 控制項無法變成使用中, 而且無法接受使用者輸入。

##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

使用下拉式方塊按鈕命令識別碼, 將字串從應用程式字串資料表複製到指定的功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*menuButton*<br/>
脫銷功能表按鈕的參考。

### <a name="return-value"></a>傳回值

一律為 TRUE。

##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

傳回清單方塊中包含指定字串之第一個專案的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
在要在清單方塊中搜尋的文字。

### <a name="return-value"></a>傳回值

專案的索引;如果找不到專案, 則為 CB_ERR, 否則為。

### <a name="remarks"></a>備註

##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

取得具有指定命令識別碼之下拉式方塊按鈕的指標。

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

*bIsFocus*<br/>
在TRUE 表示只搜尋焦點按鈕;FALSE 表示搜尋所有按鈕。

### <a name="return-value"></a>傳回值

下拉式方塊按鈕的指標;如果找不到按鈕, 則為 Null。

### <a name="remarks"></a>備註

##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

傳回下拉式方塊按鈕中下拉式方塊的指標。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>傳回值

如果方法成功, 則為[CComboBox 類別](../../mfc/reference/ccombobox-class.md)物件的指標;否則為 Null。

### <a name="remarks"></a>備註

##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetCoNtextMenuID

取得下拉式方塊按鈕的快捷方式功能表資源識別碼。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>傳回值

快捷方式功能表資源識別碼。

##  <a name="getcount"></a>CMFCToolBarComboBoxButton:: GetCount

傳回清單方塊中的專案數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

清單方塊中的專案數。

### <a name="remarks"></a>備註

##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

取得下拉式方塊按鈕的清單方塊中具有指定命令識別碼的專案數。

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

### <a name="return-value"></a>傳回值

清單方塊中的專案數;否則, 如果找不到下拉式方塊按鈕, 則 CB_ERR。

### <a name="remarks"></a>備註

##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

取得清單方塊中目前選取之專案的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

清單方塊中目前選取專案的索引;如果未選取任何專案, 則為 CB_ERR。

### <a name="remarks"></a>備註

清單方塊索引是以零為基底。

##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

傳回具有指定命令識別碼之下拉式方塊按鈕清單方塊中目前所選取專案的索引。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

### <a name="return-value"></a>傳回值

清單方塊中目前選取專案的索引;否則, 如果未選取任何專案, 或找不到下拉式方塊按鈕, 則 CB_ERR。

### <a name="remarks"></a>備註

清單方塊索引是以零為基底。

##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

傳回下拉式方塊按鈕中編輯方塊的指標。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

如果方法成功, 則為編輯方塊的指標;否則為 Null。

### <a name="remarks"></a>備註

##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

傳回下拉式方塊的視窗控制碼。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

視窗控制碼, 如果下拉式方塊未與視窗物件相關聯, 則為 Null。

##  <a name="getitem"></a>CMFCToolBarComboBoxButton:: GetItem

傳回與清單方塊中指定索引處的專案相關聯的字串。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

與專案相關聯之字串的指標。否則, 如果索引參數無效, 或索引參數為-1, 且下拉式方塊中沒有選取的專案, 則為 Null。

### <a name="remarks"></a>備註

索引參數-1 會傳回目前選取之專案的字串。

##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

傳回與具有指定命令識別碼之下拉式方塊按鈕清單方塊中指定索引處的專案相關聯的字串。

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果方法成功, 則為專案字串的指標;否則, 如果索引無效, 則找不到下拉式方塊按鈕, 或如果 index 為-1 且下拉式方塊中沒有選取的專案, 則為 Null。

### <a name="remarks"></a>備註

索引值-1 會傳回目前選取之專案的字串。

##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton:: GetItemData

傳回與清單方塊中特定索引之專案相關聯的資料。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

與專案相關聯的資料;如果專案不存在, 則為0。

### <a name="remarks"></a>備註

索引參數-1 會傳回與目前選取之專案相關聯的資料。

##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll

傳回具有特定命令識別碼之下拉式方塊按鈕清單方塊中, 與專案相關聯的資料。

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果方法成功, 則為與專案相關聯的資料;否則, 如果指定的索引無效, 則為 0, 如果找不到下拉式列示方塊按鈕, 則為 CB_ERR。

### <a name="remarks"></a>備註

索引參數-1 會傳回與目前選取之專案相關聯的資料。

##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

傳回具有特定命令識別碼之下拉式方塊按鈕清單方塊中, 與專案相關聯的資料。 此資料會以指標的形式傳回。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在下拉式方塊按鈕的命令 ID。

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果方法成功, 則為與專案相關聯的指標;否則, 如果發生錯誤, 則為-1, 如果找不到下拉式方塊按鈕, 則為 Null。

### <a name="remarks"></a>備註

##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

傳回下拉式方塊按鈕的提示字串。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>傳回值

提示字串。

### <a name="remarks"></a>備註

這個方法目前未執行。

##  <a name="gettext"></a>CMFCToolBarComboBoxButton:: GetText

取得編輯方塊中的文字。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>傳回值

編輯方塊中的文字。

### <a name="remarks"></a>備註

##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

取得下拉式方塊按鈕的編輯方塊中具有指定命令識別碼的文字。

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在特定下拉式方塊按鈕的命令 ID。

### <a name="return-value"></a>傳回值

如果方法成功, 則為編輯方塊中的文字;否則為 Null。

### <a name="remarks"></a>備註

##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

指出下拉式方塊目前是否有焦點。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

如果下拉式方塊目前具有焦點, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果下拉式方塊的任何子視窗目前具有焦點, 則這個方法也會傳回 TRUE。

##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

傳回應用程式中下拉式方塊按鈕的垂直位置。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>傳回值

如果按鈕已置中, 則為 TRUE;如果按鈕對齊在上方, 則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

傳回應用程式中下拉式方塊按鈕的平面樣式外觀。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>傳回值

如果按鈕具有平面樣式, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

下拉式方塊按鈕的預設平面樣式為 FALSE。

##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf

指出指定的控制碼是否與下拉式方塊按鈕或其中一個子系相關聯。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>參數

*hwnd*<br/>
在視窗控制碼。

### <a name="return-value"></a>傳回值

如果控制碼是以下拉式方塊按鈕或其中一個子系相關聯, 則為 TRUE;否則為 FALSE。

##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

指出下拉式方塊按鈕是否位於功能區面板上。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>傳回值

一律為 FALSE。

### <a name="remarks"></a>備註

根據預設, 這個方法一律會傳回 FALSE, 這表示下拉式方塊按鈕永遠不會顯示在功能區面板上。

##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

傳回下拉式方塊按鈕的可見度狀態。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>傳回值

下拉式方塊按鈕的可見度狀態。

##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

指出下拉式方塊按鈕是否處理訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotifyCode*<br/>
在與命令相關聯的通知訊息。

### <a name="return-value"></a>傳回值

下拉式方塊按鈕是否處理訊息。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

當按鈕新增至 [**自訂**] 對話方塊時, 由架構呼叫。

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize

由架構呼叫以計算按鈕的大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示下拉式方塊按鈕的裝置內容。

*sizeDefault*<br/>
在下拉式方塊按鈕的預設大小。

*bHorz*<br/>
在父工具列的停駐狀態。 當工具列水準停駐時為 TRUE, 而當工具列垂直停駐時為 FALSE。

### <a name="return-value"></a>傳回值

`SIZE`結構, 包含下拉式方塊按鈕的維度 (以圖元為單位)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

當下拉式方塊按鈕插入新工具列時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在新父工具列的指標。

##  <a name="onclick"></a>CMFCToolBarComboBoxButton:: OnClick

當使用者按一下下拉式方塊按鈕時由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在下拉式方塊按鈕之父視窗的指標。

*bDelay*<br/>
在保留供衍生類別使用。

### <a name="return-value"></a>傳回值

如果方法會處理事件, 則為 TRUE;否則為 FALSE。

##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor

當使用者變更父工具列色彩以設定下拉式方塊按鈕色彩時, 由架構呼叫。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示下拉式方塊按鈕的裝置內容。

*nCtlColor*<br/>
在未使用.

### <a name="return-value"></a>傳回值

架構用來繪製下拉式方塊按鈕背景之筆刷的控制碼。

### <a name="remarks"></a>備註

這個方法也會設定下拉式方塊按鈕的文字色彩。

##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw

由架構呼叫, 使用指定的樣式和選項繪製下拉式方塊按鈕。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在顯示按鈕的裝置內容。

*rect*<br/>
在按鈕的周框。

*pImages*<br/>
在與按鈕相關聯的影像集合。

*bHorz*<br/>
在父工具列的停駐狀態。 當工具列水準停駐時為 TRUE, 而當工具列垂直停駐時為 FALSE。

*bCustomizeMode*<br/>
在應用程式是否處於自訂模式。

*bHighlight*<br/>
在是否繪製反白顯示的下拉式方塊按鈕。

*bDrawBorder*<br/>
在是否要以框線繪製下拉式方塊按鈕。

*bGrayDisabledButtons*<br/>
在TRUE 表示繪製陰影停用的按鈕;FALSE 表示使用已停用的映射集合。

##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

由架構呼叫, 以在 [**自訂**] 對話方塊的 [**命令**] 窗格中繪製下拉式方塊按鈕。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示下拉式方塊按鈕的裝置內容。

*rect*<br/>
在下拉式方塊按鈕的周框。

*bSelected*<br/>
在如果已選取下拉式方塊按鈕, 則為 TRUE;否則為 FALSE。

### <a name="return-value"></a>傳回值

下拉式方塊按鈕的寬度 (以圖元為單位)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

由架構呼叫, 以在應用程式字型變更時設定下拉式方塊按鈕字型。

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

由架構呼叫, 以在父工具列移動時變更下拉式方塊按鈕的位置。

```
virtual void OnMove();
```

##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

當下拉式方塊按鈕隱藏或顯示時由架構呼叫。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
在是否要隱藏或顯示下拉式方塊按鈕。

##  <a name="onsize"></a>CMFCToolBarComboBoxButton:: OnSize

由架構呼叫, 以在父工具列變更大小時變更下拉式方塊按鈕的大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
在下拉式方塊按鈕的新寬度。

##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

當使用者變更下拉式方塊按鈕的工具提示時, 由架構呼叫。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在下拉式方塊按鈕之父視窗的指標。

*iButtonIndex*<br/>
在下拉式方塊按鈕的識別碼。

*wndToolTip*<br/>
在要與下拉式方塊按鈕產生關聯的工具提示。

*str*<br/>
在工具提示文字。

### <a name="return-value"></a>傳回值

如果方法會處理事件, 則為 TRUE;否則為 FALSE。

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

刪除清單和編輯方塊中的所有專案。

```
void RemoveAllItems();
```

### <a name="remarks"></a>備註

從清單方塊中移除所有專案, 並編輯下拉式方塊的控制項。

##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem

選取清單方塊中的專案。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。

*bNotify*<br/>
在TRUE 表示通知選取範圍的下拉式方塊按鈕;否則為 FALSE。

*dwData*<br/>
在與清單方塊中的專案相關聯的資料。

*lpszText*<br/>
在清單方塊中專案的文字。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll

在下拉式方塊按鈕的清單方塊中選取具有指定命令識別碼的專案。

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在包含清單方塊之下拉式方塊按鈕的命令 ID。

*iIndex*<br/>
在清單方塊中專案以零為基底的索引。 值為-1 會移除清單方塊中任何目前的選取範圍, 並清除編輯方塊。

*dwData*<br/>
在清單方塊中專案的資料。

*lpszText*<br/>
在清單方塊中專案的文字。

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="serialize"></a>CMFCToolBarComboBoxButton:: 序列化

從封存讀取此物件, 或將它寫入封存。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[in、out]要`CArchive`序列化的物件。

### <a name="remarks"></a>備註

物件中的`CArchive`設定會決定此方法是要讀取或寫入封存。

##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData

使用下拉式方塊`CAccessibilityData`按鈕中的協助工具資料, 填入指定的物件。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
在下拉式方塊按鈕的父視窗。

*data*<br/>
脫銷從下拉式方塊按鈕接收協助工具資料的物件。`CAccessibilityData`

### <a name="return-value"></a>傳回值

如果方法成功, 則為 TRUE;否則為 FALSE。

##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

設定應用程式中下拉式列示方塊按鈕的垂直位置。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>參數

*bCenterVert*<br/>
在TRUE 表示在工具列中置中下拉式方塊按鈕;FALSE 表示將下拉式方塊按鈕對齊工具列的頂端。

### <a name="remarks"></a>備註

根據預設, 下拉式方塊按鈕會對齊頂端。

##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetCoNtextMenuID

設定下拉式方塊按鈕的快捷方式功能表資源識別碼。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>參數

*uiResID*<br/>
在快捷方式功能表資源識別碼。

##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

在下拉時設定清單方塊的高度。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
在清單方塊的高度 (以圖元為單位)。

### <a name="remarks"></a>備註

預設高度為150圖元。

##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

設定應用程式中下拉式方塊按鈕的平面樣式外觀。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
在若為平面樣式外觀, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

下拉式方塊按鈕的預設平面樣式為 FALSE。

##  <a name="setstyle"></a>CMFCToolBarComboBoxButton:: SetStyle

設定下拉式方塊按鈕的指定樣式, 並在未停用時重新繪製控制項。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
[in]位元組合 (OR) 工具列的樣式。

### <a name="remarks"></a>備註

如需工具列按鈕樣式的清單, 請參閱[工具列控制項樣式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>CMFCToolBarComboBoxButton:: SetText

設定下拉式方塊按鈕的編輯方塊中的文字。

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
在字串的指標, 其中包含編輯方塊的文字。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)

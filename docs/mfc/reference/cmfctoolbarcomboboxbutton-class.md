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
ms.openlocfilehash: e3c124103aa95d9db5095e438a6b21d46c7cb35d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772068"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 類別

包含下拉式方塊控制項的工具列按鈕 ( [CComboBox 類別](../../mfc/reference/ccombobox-class.md))。

## <a name="syntax"></a>語法

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|建構 `CMFCToolBarComboBoxButton`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|將項目至下拉式方塊清單的結尾。|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|將下拉式方塊的清單中的項目。 在清單中項目的順序由`Compare`。|
|[CMFCToolBarComboBoxButton::Compare](#compare)|比較兩個項目。 呼叫來排序項目`AddSortedItems`將加入至下拉式方塊的清單。|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|建立新的編輯控制項的下拉式方塊按鈕。|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|從下拉式方塊的清單中刪除項目。|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|傳回包含指定的字串中的項目索引。|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|讓指標回到下拉式方塊按鈕，並提供指定的命令識別碼。|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|傳回內嵌於下拉式方塊按鈕的下拉式方塊控制項的指標。|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|在下拉式方塊中方塊的清單傳回的項目數。|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|尋找下拉式方塊按鈕具有指定的命令 id。 傳回的項目數下拉式方塊中方塊的清單，該按鈕。|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|傳回選取的項目索引下拉式方塊中方塊的清單。|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回下拉式方塊中方塊的清單，該按鈕的選取項目的索引。|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|讓指標回到編輯控制項內嵌在下拉式方塊按鈕。|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|傳回與下拉式方塊中指定的索引相關聯的字串方塊的清單。|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的字串。|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|傳回與下拉式方塊中指定的索引相關聯的 32 位元值方塊的清單。|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回該按鈕的下拉式方塊的清單中的索引相關聯的 32 位元值。|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|尋找下拉式方塊按鈕具有指定的命令 id。 擷取的 32 位元值相關聯的該按鈕，然後傳回 32 位元值的指標下拉式方塊的清單中的索引。|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|從下拉式方塊編輯控制項中傳回的文字。|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|尋找下拉式方塊按鈕具有指定的命令 ID，並傳回文字編輯控制項，該按鈕。|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|決定應用程式中的下拉式方塊按鈕要置中或與工具列的頂端對齊。|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|判斷應用程式中的下拉式方塊按鈕是否具有平面外觀。|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|移除所有項目從清單方塊和編輯下拉式方塊控制項。|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根據其索引、 32 位元值或字串，下拉式方塊中選取的項目，並通知下拉式方塊控制項，需選取項目。|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|尋找下拉式方塊按鈕具有指定的命令 id。 呼叫`SelectItem`該按鈕，根據其字串、 索引或 32 位元值的下拉式方塊中選取一個項目。|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定應用程式中的下拉式方塊按鈕會垂直置中或與工具列的頂端對齊。|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|設定下拉式清單方塊的高度。|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定應用程式中的下拉式方塊按鈕是否具有平面外觀。|

## <a name="remarks"></a>備註

若要加入工具列的下拉式方塊按鈕，請遵循下列步驟：

1. 為父工具列資源的按鈕保留假的資源 ID。

2. 建構`CMFCToolBarComboBoxButton`物件。

3. 在處理 AFX_WM_RESETTOOLBAR 訊息的訊息處理常式，假的按鈕與新的下拉式方塊按鈕使用取代[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。

如需詳細資訊，請參閱[逐步解說：將工具列上的控制項加入](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 如需下拉式方塊的工具列按鈕的範例，請參閱範例專案 VisualStudioDemo。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarComboBoxButton` 類別中使用各種方法。 此範例示範如何啟用編輯] 和 [下拉式方塊中，應用程式中設定的垂直位置下拉式方塊按鈕、 清單方塊的高度時設定拉下時，應用程式中設定的下拉式方塊按鈕的平面樣式外觀並設定在編輯方塊中的下拉式方塊按鈕的文字。 此程式碼片段是一部分[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxtoolbarcomboboxbutton.h

##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem

將唯一的項目附加至清單方塊中。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[in]要加入至清單方塊項目的文字。

*dwData*<br/>
[in]要加入至清單方塊項目相關聯的資料。

### <a name="return-value"></a>傳回值

在清單方塊中的最後一個項目索引。

### <a name="remarks"></a>備註

排序的清單方塊樣式時，請勿使用這個方法。

如果項目文字已在清單方塊中，新的資料會儲存與現有的項目。 項目的搜尋會區分大小寫。

##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem

將項目加入至清單方塊中所定義的順序[比較](#compare)方法。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[in]要加入至清單方塊項目的文字。

*dwData*<br/>
[in]要加入至清單方塊項目相關聯的資料。

### <a name="return-value"></a>傳回值

已新增至清單方塊項目的索引。

### <a name="remarks"></a>備註

使用此函式項目加入清單方塊中，以特定順序。

##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched

指出是否可以變更下拉式方塊按鈕的大小。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

會傳回 TRUE。

##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

建構[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[in][新增] 按鈕的命令識別碼。

*iImage*<br/>
[in][新增] 按鈕相關聯的映像的映像索引。

*dwStyle*<br/>
[in][新增] 按鈕的樣式。

*iWidth*<br/>
[in]寬度，單位為像素的 [新增] 按鈕。

### <a name="remarks"></a>備註

預設寬度是 150 個像素。

如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData

刪除使用者定義的資料。

```
virtual void ClearData();
```

### <a name="remarks"></a>備註

依預設這個方法沒有任何作用。 如果您想要刪除使用者定義的任何資料，請覆寫這個方法在衍生類別中。

##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare

比較兩個字串。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>參數

*lpszItem1*<br/>
[in]要比較的第一個字串。

*lpszItem2*<br/>
[in]要比較的第二個字串。

### <a name="return-value"></a>傳回值

值，指出字串之間的區分大小寫字母關聯性。 下表列出可能的值：

|值|描述|
|-----------|-----------------|
|\<0|第一個字串小於第二個。|
|0|第一個字串等於第二個。|
|>0|第一個字串大於第二個。|

### <a name="remarks"></a>備註

覆寫這個方法，以變更項目在清單方塊中的排序方式。

比較會區分大小寫。

這個方法只會從呼叫[AddSortedItem](#addsorteditem)方法。

##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom

複製指定的狀態`CMFCToolBarComboBoxButton`目前的物件。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]來源`CMFCToolBarComboBoxButton`物件。

##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo

建立新的下拉式方塊的下拉式方塊按鈕。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]按鈕的父視窗指標。

*rect*<br/>
[in]在下拉式方塊的周框。

### <a name="return-value"></a>傳回值

變數的指標，如果方法成功，新下拉式方塊否則為 NULL。

##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit

建立新的編輯方塊的下拉式方塊按鈕。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]按鈕的父視窗指標。

*rect*<br/>
[in]新的編輯方塊的週框。

*dwEditStyle*<br/>
[in]新的編輯方塊控制項樣式。

### <a name="return-value"></a>傳回值

如果方法成功，新的指標] 編輯方塊否則為 NULL。

### <a name="remarks"></a>備註

建立新的編輯方塊的下拉式方塊按鈕時，架構會呼叫這個方法。 覆寫此方法以變更如何[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)建立。

##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem

從清單方塊中，刪除指定的項目。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
  BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]要刪除之項目的以零為起始的索引。

*dwData*<br/>
[in]要刪除的項目相關聯的資料。

*lpszText*<br/>
[in]要刪除之項目的文字。 如果有多個相同的文字項目，則會刪除第一個項目。

### <a name="return-value"></a>傳回值

如果已找到項目，並將其已成功刪除;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

重複的項目使用者定義的資料。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>備註

依預設這個方法沒有任何作用。 如果您想要複製的任何使用者定義資料，請覆寫這個方法在衍生類別中。

##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow

啟用或停用編輯] 和 [下拉式方塊。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]若要啟用編輯和下拉式方塊中，則為 TRUE若要停用編輯] 和 [下拉式方塊，則為 FALSE。

### <a name="remarks"></a>備註

停用時，這些控制項不能成為使用中，而且不能接受使用者輸入。

##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton

複本識別碼的應用程式字串資料表中指定的功能表，使用下拉式方塊按鈕命令的字串。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*menuButton*<br/>
[out]功能表按鈕的參考。

### <a name="return-value"></a>傳回值

永遠為 TRUE。

##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem

傳回包含指定的字串清單方塊中的第一個項目的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[in]要在清單方塊中搜尋文字。

### <a name="return-value"></a>傳回值

項目的索引或 CB_ERR 如果找不到項目。

### <a name="remarks"></a>備註

##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd

取得具有指定的命令識別碼。 下拉式方塊按鈕的指標

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

*bIsFocus*<br/>
[in]若為 true，則只搜尋已取得焦點按鈕;搜尋所有按鈕，則為 FALSE。

### <a name="return-value"></a>傳回值

下拉式方塊按鈕; 指標或者，如果找不到按鈕，則為 NULL。

### <a name="remarks"></a>備註

##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox

讓指標回到下拉式方塊中下拉式方塊按鈕。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>傳回值

指標[CComboBox 類別](../../mfc/reference/ccombobox-class.md)物件的方法是否成功; 否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID

取得下拉式方塊按鈕的捷徑功能表資源識別碼。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>傳回值

快顯功能表資源識別碼。

##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount

在清單方塊中，傳回的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

在清單方塊中的項目數目。

### <a name="remarks"></a>備註

##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll

取得具有指定之命令識別碼的下拉式方塊按鈕的清單方塊中的項目數目

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

在清單方塊中的項目數否則，如果下拉式方塊按鈕的 CB_ERR 找不到。

### <a name="remarks"></a>備註

##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel

在清單方塊中，取得目前選取項目的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

在清單方塊中目前選取項目的索引或 CB_ERR 如果在不選取任何項目。

### <a name="remarks"></a>備註

清單方塊索引以零為起始。

##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll

傳回目前選取項目的索引中的下拉式清單方塊] 按鈕具有指定的命令 id。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

在清單方塊中目前選取項目的索引否則，CB_ERR 如果在不選取任何項目或下拉式方塊按鈕找不到。

### <a name="remarks"></a>備註

清單方塊索引以零為起始。

##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl

讓指標回到編輯方塊在下拉式方塊按鈕。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

變數的指標，如果方法成功; 中的 [編輯] 方塊否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd

傳回下拉式方塊的視窗控制代碼。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

視窗控制代碼或如果不是視窗物件相關聯的下拉式方塊則為 NULL。

##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem

傳回字串與清單方塊中的指定索引處的項目相關聯。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

項目; 相關聯的字串指標否則，如果索引參數無效，或者索引參數是-1，下拉式方塊中沒有選取項目可為 NULL。

### <a name="remarks"></a>備註

索引參數-1 會傳回目前選取之項目的字串。

##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll

傳回具有指定之命令識別碼的下拉式方塊按鈕的清單方塊中的指定索引處的項目相關聯的字串

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

如果方法成功; 的項目的字串的指標否則，如果索引是無效的 NULL，下拉式方塊按鈕找不到，或者索引是-1，下拉式方塊中沒有選取項目。

### <a name="remarks"></a>備註

索引值-1 會傳回目前選取之項目的字串。

##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData

傳回與清單方塊中的特定索引處的項目相關聯的資料。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

與項目; 相關聯的資料或 0，如果項目不存在。

### <a name="remarks"></a>備註

索引參數-1 會傳回目前選取的項目相關聯的資料。

##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll

傳回具有特定的命令識別碼。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

如果方法成功; 與項目相關聯的資料如果指定的索引無效，或找不到 CB_ERR 如果下拉式方塊按鈕，否則為 0。

### <a name="remarks"></a>備註

索引參數-1 會傳回目前選取的項目相關聯的資料。

##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll

傳回具有特定的命令識別碼。 下拉式方塊按鈕的清單方塊中的特定索引處的項目相關聯的資料 這項資料會傳回的指標。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]下拉式方塊按鈕的命令識別碼。

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

### <a name="return-value"></a>傳回值

如果方法成功; 相關聯的項目指標否則，-1，如果錯誤發生時，或找不到如果下拉式方塊按鈕則為 NULL。

### <a name="remarks"></a>備註

##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt

傳回提示字串的下拉式方塊按鈕。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>傳回值

提示的字串。

### <a name="remarks"></a>備註

這個方法目前尚未實作。

##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText

取得文字編輯方塊中。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>傳回值

在編輯方塊中的文字。

### <a name="remarks"></a>備註

##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll

取得具有指定之命令識別碼的下拉式方塊按鈕的編輯方塊中的文字

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]特定的下拉式方塊按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

如果方法成功; 中的 [編輯] 方塊中的文字否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus

表示下拉式方塊是否目前具有焦點。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

如果下拉式方塊目前具有焦點，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

如果下拉式方塊的任何子視窗目前具有焦點，這個方法也會傳回 TRUE。

##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert

傳回應用程式中的下拉式方塊按鈕的垂直位置。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>傳回值

如果會置中按鈕;，則為 TRUE。如果按鈕靠上對齊，則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode

傳回應用程式中的下拉式方塊按鈕的平面樣式外觀。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>傳回值

如果按鈕有一般樣式;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

下拉式方塊按鈕的預設一般樣式為 FALSE。

##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf

指出指定的控制代碼是否與下拉式方塊按鈕，或其中一個子系相關聯。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>參數

*hwnd*<br/>
[in]視窗控制代碼。

### <a name="return-value"></a>傳回值

如果控制代碼與下拉式方塊按鈕，或其中一個子系; 相關聯，則為 TRUE。否則為 FALSE。

##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton

表示下拉式方塊按鈕是否位於功能區面板。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>傳回值

永遠為 FALSE。

### <a name="remarks"></a>備註

根據預設，這個方法一律會傳回 FALSE，表示下拉式方塊按鈕永遠不會顯示在功能區面板上。

##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible

傳回可見性狀態的下拉式方塊按鈕。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>傳回值

下拉式方塊按鈕的可見性狀態。

##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand

表示下拉式方塊按鈕是否處理訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotifyCode*<br/>
[in]與命令相關聯的通知訊息。

### <a name="return-value"></a>傳回值

下拉式方塊按鈕是否會處理訊息。

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage

加入按鈕時由架構呼叫**自訂**] 對話方塊。

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
[in]裝置內容會顯示下拉式方塊按鈕。

*sizeDefault*<br/>
[in]下拉式方塊按鈕的預設大小。

*bHorz*<br/>
[in]為父工具列停駐狀態。 工具列停駐時以水平和 FALSE 以垂直方式停駐工具列時，則為 TRUE。

### <a name="return-value"></a>傳回值

A`SIZE`結構，其中包含下拉式方塊按鈕，像素為單位的維度。

##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd

插入新的工具列下拉式方塊按鈕時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]在新的父工具列的指標。

##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick

當使用者按下下拉式方塊按鈕時由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]下拉式方塊按鈕的父視窗的指標。

*bDelay*<br/>
[in]保留供衍生類別中使用。

### <a name="return-value"></a>傳回值

如果此方法會處理事件，則為 TRUE否則為 FALSE。

##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor

當使用者變更父工具列色彩設定下拉式方塊按鈕的色彩，由架構呼叫。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容會顯示下拉式方塊按鈕。

*nCtlColor*<br/>
[in]未使用。

### <a name="return-value"></a>傳回值

架構會使用來繪製下拉式方塊按鈕背景的筆刷的控制代碼。

### <a name="remarks"></a>備註

這個方法也會設定下拉式方塊按鈕文字色彩。

##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw

由架構呼叫以繪製下拉式方塊按鈕，使用指定的樣式和選項。

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
[in]裝置內容，顯示的按鈕。

*rect*<br/>
[in]按鈕的週框。

*pImages*<br/>
[in]與按鈕關聯的映像集合。

*bHorz*<br/>
[in]為父工具列停駐狀態。 工具列停駐時以水平和 FALSE 以垂直方式停駐工具列時，則為 TRUE。

*bCustomizeMode*<br/>
[in]應用程式是否以自訂模式。

*bHighlight*<br/>
[in]是否要繪製反白顯示下拉式方塊按鈕。

*bDrawBorder*<br/>
[in]是否要繪製框線的下拉式方塊按鈕。

*bGrayDisabledButtons*<br/>
[in]若為 true，則繪製陰影表示停用的按鈕;如果為 false，則使用已停用的映像集合。

##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

由架構呼叫以繪製下拉式方塊按鈕**命令**窗格**自訂**] 對話方塊。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容會顯示下拉式方塊按鈕。

*rect*<br/>
[in]下拉式方塊按鈕的週框。

*bSelected*<br/>
[in]如果已選取下拉式方塊按鈕;，則為 TRUE。否則為 FALSE。

### <a name="return-value"></a>傳回值

寬度，單位為像素下拉式方塊按鈕。

##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged

由架構呼叫以設定下拉式方塊按鈕的字型，應用程式字型變更時。

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove

由架構呼叫以變更下拉式方塊按鈕的位置，為父工具列移動時。

```
virtual void OnMove();
```

##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow

隱藏或顯示下拉式方塊按鈕時由架構呼叫。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
[in]是否要隱藏或顯示下拉式方塊按鈕。

##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize

由架構呼叫以變更下拉式方塊按鈕的大小，為父工具列大小變更時。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
[in]下拉式方塊按鈕的新寬度。

##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip

當使用者變更下拉式方塊按鈕的工具提示時，由架構呼叫。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]下拉式方塊按鈕的父視窗的指標。

*iButtonIndex*<br/>
[in]下拉式方塊按鈕的識別碼。

*wndToolTip*<br/>
[in]下拉式方塊按鈕相關聯的工具提示。

*str*<br/>
[in]工具提示文字。

### <a name="return-value"></a>傳回值

如果此方法會處理事件，則為 TRUE否則為 FALSE。

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

從清單] 和 [編輯方塊中，刪除所有項目。

```
void RemoveAllItems();
```

### <a name="remarks"></a>備註

移除所有項目從清單方塊和編輯下拉式方塊控制項。

##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem

在清單方塊中選取項目。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[in]清單方塊中的項目以零為起始的索引。

*bNotify*<br/>
[in]TRUE 表示通知下拉式方塊按鈕的選取項目;否則為 FALSE。

*dwData*<br/>
[in]使用清單方塊中的項目相關聯的資料。

*lpszText*<br/>
[in]在清單方塊項目的文字。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll

選取的項目在清單方塊的下拉式方塊按鈕具有指定的命令 id。

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
[in]包含在清單方塊的下拉式方塊按鈕的命令識別碼。

*iIndex*<br/>
[in]在清單方塊中的項目以零為起始的索引。 -1 值的清單方塊中移除任何目前的選取範圍，並清除 [編輯] 方塊。

*dwData*<br/>
[in]清單方塊中的項目資料。

*lpszText*<br/>
[in]在清單方塊項目的文字。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize

從封存讀取這個物件，或將其寫入至封存。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[in、 out]`CArchive`来序列化的物件。

### <a name="remarks"></a>備註

在 [設定`CArchive`物件決定這個方法會讀取或寫入封存。

##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData

填入指定`CAccessibilityData`藉由從下拉式方塊按鈕的協助工具資料的物件。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[in]下拉式方塊按鈕的父視窗。

*data*<br/>
[out]A`CAccessibilityData`收到下拉式方塊按鈕的協助工具資料的物件。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert

應用程式中設定下拉式方塊按鈕的垂直位置。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>參數

*bCenterVert*<br/>
[in]TRUE 表示置中下拉式方塊按鈕的工具列，如果為 false，則對齊下拉式方塊按鈕加入工具列頂端。

### <a name="remarks"></a>備註

根據預設，頂端對齊下拉式方塊按鈕。

##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID

設定下拉式方塊按鈕的捷徑功能表資源識別碼。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>參數

*uiResID*<br/>
[in]快顯功能表資源識別碼。

##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight

向下拖曳時，請設定清單方塊的高度。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
[in]像素為單位，清單方塊的高度。

### <a name="remarks"></a>備註

預設高度為 150 個像素。

##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode

應用程式中設定下拉式方塊按鈕的平面樣式的外觀。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
[in]平面樣式外觀;，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

下拉式方塊按鈕的預設一般樣式為 FALSE。

##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle

設定指定的樣式的下拉式方塊按鈕，並重新繪製控制項，如果未停用。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
[in]位元組合 (OR) 工具列的樣式。

### <a name="remarks"></a>備註

如需工具列按鈕樣式的清單，請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText

設定中的文字編輯方塊的下拉式方塊按鈕。

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[in]字串，包含編輯方塊的文字指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)

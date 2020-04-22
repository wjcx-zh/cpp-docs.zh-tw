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
ms.openlocfilehash: 995d7d0db55889130e1cad9585b8fc87285ffd27
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754021"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 類別

包含組合框控制件( [CComboBox 類](../../mfc/reference/ccombobox-class.md)) 的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarComBox按鈕:CMFC工具列按鈕](#cmfctoolbarcomboboxbutton)|建構 `CMFCToolBarComboBoxButton`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarComBox按鈕::新增專案](#additem)|將專案添加到組合框清單的末尾。|
|[CMFCToolBarComBox按鈕::新增排序專案](#addsorteditem)|將專案添加到組合框清單中。 清單中順序由 指定`Compare`。|
|[CMFCToolBarComBox按鈕::比較](#compare)|比較兩個專案。 呼叫以對`AddSortedItems`新增到組合框清單的項目進行排序。|
|[CMFCToolBarComBox按鈕::建立編輯](#createedit)|為組合框按鈕創建新的編輯控制項。|
|[CMFCToolBarComBox按鈕::Delete專案](#deleteitem)|從組合框清單中移除專案。|
|[CMFCToolBarComBox按鈕::尋找專案](#finditem)|返回包含指定字串的項索引。|
|[CMFCToolBarComBox按鈕::獲取](#getbycmd)|返回指向具有指定命令 ID 的組合框按鈕的指標。|
|[CMFCToolBarComBox按鈕::獲取康博盒](#getcombobox)|返回嵌入在組合框按鈕中的組合框控件的指標。|
|[CMFCToolBarComBox按鈕::取得計數](#getcount)|傳回組合框清單中的項目數。|
|[CMFCToolBarComBox按鈕::獲取計數所有](#getcountall)|尋找具有指定命令 ID 的組合框按鈕。 返回該按鈕的組合框清單中的項目數。|
|[CMFCToolBarComBox按鈕::取得CurSel](#getcursel)|返回組合框清單中所選項的索引。|
|[CMFCToolBarComBox按鈕::取得CurSelAll](#getcurselall)|尋找具有指定命令 ID 的組合框按鈕,並在該按鈕的組合框清單中傳回所選項的索引。|
|[CMFCToolBarComBox按鈕::取得編輯](#geteditctrl)|返回指向嵌入在組合框按鈕中的編輯控制項的指標。|
|[CMFCToolBarComBox按鈕::獲取專案](#getitem)|傳回與組合框清單中的指定索引關聯的字串。|
|[CMFCToolBarComBox按鈕::獲取專案全部](#getitemall)|尋找具有指定命令 ID 的組合框按鈕,並傳回這個按鈕的組合框清單中與索引關聯的字串。|
|[CMFCToolBarComBox按鈕::獲取項目數據](#getitemdata)|返回與組合框清單中的指定索引關聯的 32 位值。|
|[CMFCToolBarCombox按鈕:取得項目數據全部](#getitemdataall)|尋找具有指定命令 ID 的組合框按鈕,並傳回這個按鈕的組合框清單中與索引關聯的 32 位值。|
|[CMFCToolBarComBox按鈕::獲取項目數據PtrAll](#getitemdataptrall)|尋找具有指定命令 ID 的組合框按鈕。 檢索在該按鈕的組合框列表中關聯的索引的 32 位值,並將 32 位值作為指標返回。|
|[CMFCToolBarComBox按鈕::獲取文本](#gettext)|從組合框的編輯控制件返回文本。|
|[CMFCToolBarComBox按鈕::獲取文本全部](#gettextall)|尋找具有指定命令 ID 的組合框按鈕,並從該按鈕的編輯控制項返回文本。|
|[CMFCToolBarComBox按鈕::IsCenterVert](#iscentervert)|確定應用程式中的組合框按鈕是居中還是與工具列頂部對齊。|
|[CMFCToolBarComBox按鈕::是平模式](#isflatmode)|確定應用程式中的組合框按鈕的外觀是否平坦。|
|[CMFCToolBarComBox按鈕::刪除所有專案](#removeallitems)|從清單框中移除所有專案,並編輯組合框控制項。|
|[CMFCToolBarComBox按鈕::選擇專案](#selectitem)|根據組合框中的索引、32 位值或字串選擇項,並通知組合框控件有關所選內容。|
|[CMFCToolBarComBox按鈕::選擇專案全部](#selectitemall)|尋找具有指定命令 ID 的組合框按鈕。 呼叫`SelectItem`以根據該按鈕的字串、索引或 32 位值選擇該按鈕的組合框中的項。|
|[CMFCToolBarComBox按鈕::設置中心](#setcentervert)|指定應用程式中的組合框按鈕是垂直居中還是與工具列頂部對齊。|
|[CMFCToolBarCombox按鈕::設定下拉高度](#setdropdownheight)|設定下拉清單框的高度。|
|[CMFCToolBarComBox按鈕::設定平模式](#setflatmode)|指定應用程式中的組合框按鈕的外觀是否平坦。|

## <a name="remarks"></a>備註

要向工具列加入組合框按鈕,請按照以下步驟操作:

1. 為父工具列資源的按鈕保留假的資源 ID。

2. 構造`CMFCToolBarComboBoxButton`物件。

3. 在處理AFX_WM_RESETTOOLBAR消息的消息處理程式中,使用[CMFCToolBar:::替換Button,](../../mfc/reference/cmfctoolbar-class.md#replacebutton)將虛擬按鈕替換為新的組合框按鈕。

有關詳細資訊,請參閱[演練:將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 有關組合框工具列按鈕的範例,請參閱範例專案 VisualStudioDemo。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarComboBoxButton` 類別中使用各種方法。 該範例展示如何啟用編輯和組合框,設定應用程式中組合框按鈕的垂直位置,在下放清單框時設置清單框的高度,設置應用程式中組合框按鈕的平面樣式外觀,並在組合框按鈕的編輯框中設置文本。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按鈕](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbarcombox 按鈕.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComBox按鈕::新增專案

將唯一專案追加到清單框。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[在]要加入清單盒的項目的文字。

*dwData*<br/>
[在]與要添加到清單框的項關聯的數據。

### <a name="return-value"></a>傳回值

清單框中最後一項的索引。

### <a name="remarks"></a>備註

對清單框樣式進行排序時,請勿使用此方法。

如果專案文本已在清單框中,則新數據存儲與現有項一起。 對該專案的搜索區分大小寫。

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComBox按鈕::新增排序專案

按[比較](#compare)方法定義的順序將項添加到清單框。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
[在]要加入清單盒的項目的文字。

*dwData*<br/>
[在]與要添加到清單框的項關聯的數據。

### <a name="return-value"></a>傳回值

添加到列表框的項索引。

### <a name="remarks"></a>備註

使用此函數按特定順序將專案添加到清單框。

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComBox按鈕::可以拉伸

指示組合框按鈕大小是否可以更改。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

返回 TRUE。

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComBox按鈕:CMFC工具列按鈕

建構[CMFCToolBarComBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]新按鈕的命令 ID。

*i 影像*<br/>
[在]與新按鈕關聯的圖像的圖像索引。

*dwStyle*<br/>
[在]新按鈕的樣式。

*iWidth*<br/>
[在]新按鈕的寬度(以像素為單位)。

### <a name="remarks"></a>備註

默認寬度為 150 圖元。

有關工具列按鈕樣式的清單,請參閱[工具列控制元件樣式](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComBox按鈕::清除資料

刪除使用者定義的數據。

```
virtual void ClearData();
```

### <a name="remarks"></a>備註

默認情況下,此方法不執行任何操作。 如果要刪除任何使用者定義的數據,請覆蓋派生類中的此方法。

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComBox按鈕::比較

比較兩個字串。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>參數

*lpszItem1*<br/>
[在]要比較的第一個字串。

*lpszItem2*<br/>
[在]要比較的第二個字串。

### <a name="return-value"></a>傳回值

指示字串之間的區分大小寫字典關係的值。 下表列出可能的值：

|值|描述|
|-----------|-----------------|
|\<0|第一個字串小於第二個字串。|
|0|第一個字串等於第二個字串。|
|>0|第一個字串大於第二個字串。|

### <a name="remarks"></a>備註

重寫此方法以更改在清單框中排序專案的方式。

比較區分大小寫。

此方法僅從[AddSortedItem](#addsorteditem)方法調用。

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarCombox按鈕::從複製

將指定的`CMFCToolBarComboBoxButton`狀態複製到當前物件。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]源`CMFCToolBarComboBoxButton`物件。

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComBox按鈕::創建康博

為組合框按鈕創建新組合框。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向按鈕的父視窗的指標。

*矩形*<br/>
[在]組合框的邊界矩形。

### <a name="return-value"></a>傳回值

如果方法成功,則指向新組合框的指標;否則,NULL。

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComBox按鈕::建立編輯

為組合框按鈕創建新的編輯框。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向按鈕的父視窗的指標。

*矩形*<br/>
[在]新編輯框的邊界矩形。

*dwEdit 風格*<br/>
[在]控制新編輯框的樣式。

### <a name="return-value"></a>傳回值

如果方法成功,則指向新編輯框的指標;否則,NULL。

### <a name="remarks"></a>備註

當框架為組合框按鈕創建新的編輯框時,它將調用此方法。 重寫此方法以更改創建[CMFCToolBarCombox 編輯](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)的方式。

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComBox按鈕::Delete專案

從清單框中刪除指定的專案。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]要刪除的項的零基索引。

*dwData*<br/>
[在]與要刪除的項關聯的數據。

*lpszText*<br/>
[在]要刪除的項目的文本。 如果有多個具有相同文本的項,則刪除第一個專案。

### <a name="return-value"></a>傳回值

如果專案已找到並成功刪除,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComBox按鈕::D

複製使用者定義的數據。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>備註

默認情況下,此方法不執行任何操作。 如果要複製任何使用者定義的數據,請覆蓋派生類中的此方法。

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComBox按鈕::啟用視窗

啟用或禁用編輯和組合框。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 啟用編輯和組合框;FALSE 以關閉編輯和組合框。

### <a name="remarks"></a>備註

禁用后,控件無法變為活動狀態,並且無法接受用戶輸入。

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarCombox按鈕::匯出到選單按鈕

使用組合框按鈕命令 ID 將字串從應用程式字串表複製到指定的功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*選單按鈕*<br/>
[出]引用功能表按鈕。

### <a name="return-value"></a>傳回值

一律為 TRUE。

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComBox按鈕::尋找專案

傳回清單框中包含指定字串的第一項的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[在]要在清單框中搜尋的文字。

### <a name="return-value"></a>傳回值

項的索引;或CB_ERR(如果找不到該專案)。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComBox按鈕::獲取

獲取指向具有指定命令 ID 的組合框按鈕的指標。

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

*bIsFocus*<br/>
[在]TRUE 僅搜索焦點按鈕;FALSE 以搜索所有按鈕。

### <a name="return-value"></a>傳回值

指向組合框按鈕的指標;或 NULL,如果找不到按鈕。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComBox按鈕::獲取康博盒

返回組合框按鈕中組合框的指標。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>傳回值

如果方法成功,則指向[CComboBox 類](../../mfc/reference/ccombobox-class.md)物件的指標;否則 NULL。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComBox按鈕::取得上下文選單ID

獲取組合框按鈕的快捷功能表資源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>傳回值

快捷功能表資源 ID。

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComBox按鈕::取得計數

傳回清單框中的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

清單框中的項目數。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComBox按鈕::獲取計數所有

取得具有指定命令 ID 的組合框按鈕的清單框中的項目數。

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

### <a name="return-value"></a>傳回值

清單框中的項目數;否則,如果未找到組合框按鈕,則CB_ERR。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComBox按鈕::取得CurSel

在清單框中獲取當前選定項的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

清單框中選取的索引;或未選擇專案CB_ERR。

### <a name="remarks"></a>備註

清單框索引基於零。

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComBox按鈕::取得CurSelAll

在具有指定命令 ID 的組合框按鈕的清單框中傳回目前選定項的索引。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

### <a name="return-value"></a>傳回值

清單框中選取的索引;否則,如果未選擇任何專案或找不到組合框按鈕,則CB_ERR。

### <a name="remarks"></a>備註

清單框索引基於零。

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComBox按鈕::取得編輯

在組合框按鈕中返回指向編輯框的指標。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>傳回值

如果方法成功,則指向編輯框的指標;否則,NULL。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComBox按鈕::GetHwnd

返回組合框的視窗句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

如果組合框未與視窗物件關聯,則視窗句柄或 NULL。

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComBox按鈕::獲取專案

傳回與清單框中指定索引處的項目關聯的字串。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

指向與項關聯的字串的指標;否則,如果索引參數無效,或者索引參數為 -1 且組合框中沒有選定項,則 NULL。

### <a name="remarks"></a>備註

索引參數 -1 傳回目前選擇的項目的字串。

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComBox按鈕::獲取專案全部

在具有指定命令 ID 的組合框按鈕的清單框中傳回與指定索引處的項目關聯的字串。

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

如果方法成功,則指向項字串的指標;否則,如果索引無效,則 NULL,找不到組合框按鈕,或者如果索引為 -1,並且組合框中沒有選定項。

### <a name="remarks"></a>備註

索引值 -1 傳回目前選擇的項目的字串。

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComBox按鈕::獲取項目數據

返回與列表框中特定索引處的項關聯的數據。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

與項關聯的數據;或 0,如果專案不存在。

### <a name="remarks"></a>備註

索引參數 -1 返回與當前選定項關聯的數據。

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarCombox按鈕:取得項目數據全部

在具有特定命令 ID 的組合框按鈕的清單框中傳回與特定索引項關聯的數據。

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

如果方法成功,則與項關聯的數據;否則,如果指定的索引無效,則為 0;如果未找到組合框按鈕,則CB_ERR。

### <a name="remarks"></a>備註

索引參數 -1 返回與當前選定項關聯的數據。

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComBox按鈕::獲取項目數據PtrAll

在具有特定命令 ID 的組合框按鈕的清單框中傳回與特定索引項關聯的數據。 此數據作為指標返回。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]組合框按鈕的命令 ID。

*iIndex*<br/>
[在]清單框中項的零基索引。

### <a name="return-value"></a>傳回值

如果方法成功,則與項關聯的指標;否則,如果發生錯誤,則為 -1;如果未找到組合框按鈕,則為 NULL。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComBox按鈕::獲取提示

傳回組合框按鈕的提示字串。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>傳回值

提示字串。

### <a name="remarks"></a>備註

此方法當前未實現。

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComBox按鈕::獲取文本

取得編輯框中的文字。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>傳回值

編輯框中的文字。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComBox按鈕::獲取文本全部

取得具有指定命令 ID 的組合框按鈕的編輯框中的文字。

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]特定組合框按鈕的命令 ID。

### <a name="return-value"></a>傳回值

如果方法成功,則編輯框中的文本;否則,NULL。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComBox按鈕::有焦點

指示組合框當前是否具有焦點。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

如果組合框當前具有焦點,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果組合框的任何子視窗當前具有焦點,則此方法也會返回 TRUE。

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComBox按鈕::IsCenterVert

返回應用程式中組合框按鈕的垂直位置。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>傳回值

如果按鈕居中,則為 TRUE;如果按鈕在頂部對齊,則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComBox按鈕::是平模式

返回應用程序中組合框按鈕的平面樣式外觀。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>傳回值

如果按鈕具有平面樣式,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

組合框按鈕的預設平面樣式為 FALSE。

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarCombox按鈕:擁有者

指示指定的句柄是否與組合框按鈕或其子控點之一相關聯。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>參數

*霍恩德*<br/>
[在]視窗句柄。

### <a name="return-value"></a>傳回值

如果手柄與組合框按鈕或其一個子按鈕一起被壓縮,則為 TRUE;否則,FALSE。

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComBox按鈕::正帶按鈕

指示組合框按鈕是否駐留在功能區面板上。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>傳回值

一律為 FALSE。

### <a name="remarks"></a>備註

默認情況下,此方法始終返回 FALSE,這意味著組合框按鈕永遠不會顯示在功能區面板上。

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComBox按鈕::視窗可見

返回組合框按鈕的可見性狀態。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>傳回值

組合框按鈕的可見性狀態。

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComBox按鈕::通知命令

指示組合框按鈕是否處理該消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotify代碼*<br/>
[在]與命令關聯的通知消息。

### <a name="return-value"></a>傳回值

組合框按鈕是否處理消息。

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarCombox按鈕::在「添加」上自定義頁面

將按鈕添加到 **「自訂」** 對話框時由框架調用。

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarCombox按鈕::在計算尺寸上

由框架調用以計算按鈕的大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示組合框按鈕的設備上下文。

*預設*<br/>
[在]組合框按鈕的預設大小。

*布霍茲*<br/>
[在]父工具列的停靠狀態。 當工具列水平停靠時為 TRUE;當工具列垂直停靠時為 FALSE。

### <a name="return-value"></a>傳回值

包含`SIZE`組合框按鈕的尺寸(以像素為單位)的結構。

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarCombox按鈕::打開更改家長

當組合框按鈕插入到新的工具列中時,由框架調用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向新父工具列的指標。

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarCombox按鈕::點擊

當用戶按下組合框按鈕時由框架調用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]指向組合框按鈕的父視窗。

*bDelay*<br/>
[在]保留用於派生類。

### <a name="return-value"></a>傳回值

如果方法處理事件,則為 TRUE;如果方法處理事件,則為 TRUE。否則,FALSE。

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarCombox按鈕::在CtlColor上

當使用者更改父工具列顏色以設置組合框按鈕顏色時,由框架調用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示組合框按鈕的設備上下文。

*nCtlColor*<br/>
[在]閑置。

### <a name="return-value"></a>傳回值

處理框架用於繪製組合框按鈕背景的畫筆。

### <a name="remarks"></a>備註

此方法還設定組合框按鈕文字顏色。

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarCombox按鈕::開拉

框架呼叫使用指定的樣式和選項繪製組合框按鈕。

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
[在]顯示按鈕的設備上下文。

*矩形*<br/>
[在]按鈕的邊界矩形。

*pImage*<br/>
[在]與按鈕關聯的圖像的集合。

*布霍茲*<br/>
[在]父工具列的停靠狀態。 當工具列水平停靠時為 TRUE;當工具列垂直停靠時為 FALSE。

*b 客製模式*<br/>
[在]應用程式是否處於自定義模式。

*b 高光*<br/>
[在]是否繪製突出顯示的組合框按鈕。

*bDraw邊框*<br/>
[在]是否使用邊框繪製組合框按鈕。

*b 格雷關閉按鈕*<br/>
[在]TRUE 以繪製帶實線禁用的按鈕;FALSE 用於使用禁用的圖像集合。

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarCombox按鈕::在畫上定製清單

由框架呼叫以在 **「自訂」** 對話框的 **「命令」** 窗格中繪製組合框按鈕。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示組合框按鈕的設備上下文。

*矩形*<br/>
[在]組合框按鈕的邊界矩形。

*b選定*<br/>
[在]如果選擇了組合框按鈕,則為 TRUE;如果選擇了組合框按鈕,則為 TRUE。否則,FALSE。

### <a name="return-value"></a>傳回值

組合框按鈕的寬度(以像素為單位)。

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarCombox按鈕::在全域字體上更改

當應用程式字型更改時,框架呼叫以設置組合框按鈕字型。

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarCombox按鈕::移動

框架呼叫以在父工具列移動時更改組合框按鈕的位置。

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarCombox按鈕::上展

當隱藏或顯示組合框按鈕時,由框架調用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]是隱藏還是顯示組合框按鈕。

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarCombox按鈕::打開尺寸

框架呼叫以在父工具列更改大小時更改組合框按鈕的大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
[在]組合框按鈕的新寬度。

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarCombox按鈕::更新工具提示

當使用者更改組合框按鈕的工具提示時,由框架調用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向組合框按鈕的父視窗。

*iButtonIndex*<br/>
[在]組合框按鈕的 ID。

*wndToolTip*<br/>
[在]要與組合框按鈕關聯的工具提示。

*Str*<br/>
[在]工具提示文字。

### <a name="return-value"></a>傳回值

如果方法處理事件,則為 TRUE;如果方法處理事件,則為 TRUE。否則,FALSE。

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComBox按鈕::刪除所有專案

從清單和編輯框中刪除所有專案。

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>備註

從清單框中移除所有專案,並編輯組合框控制項。

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComBox按鈕::選擇專案

在清單框中選擇專案。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
[在]清單框中項的零基索引。

*b 通知*<br/>
[在]TRUE 以通知所選內容的組合框按鈕;否則 FALSE。

*dwData*<br/>
[在]與列表框中的項目關聯的數據。

*lpszText*<br/>
[在]清單框中項目的文字。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComBox按鈕::選擇專案全部

在具有指定命令 ID 的組合框按鈕的清單框中選擇專案。

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

*烏伊Cmd*<br/>
[在]包含清單框的組合框按鈕的命令 ID。

*iIndex*<br/>
[在]清單框中項的零基索引。 值 -1 刪除清單框中的任何當前選擇並清除編輯框。

*dwData*<br/>
[在]清單框中項目的資料。

*lpszText*<br/>
[在]清單框中項目的文字。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComBox按鈕:序列化

從存檔中讀取此物件或將其寫入存檔。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[進出]要`CArchive`序列化的物件。

### <a name="remarks"></a>備註

物件中的`CArchive`設置確定此方法是讀取還是寫入存檔。

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComBox按鈕::設定ACC數據

使用組合框按鈕`CAccessibilityData`中的輔助功能數據填充指定物件。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
[在]組合框按鈕的父視窗。

*資料*<br/>
[出]從`CAccessibilityData`組合框按鈕接收輔助功能數據的物件。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComBox按鈕::設置中心

設置應用程式中組合框按鈕的垂直位置。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>參數

*b中心弗特*<br/>
[在]TRUE 以將組合框按鈕居中以工具列為中心;FALSE 將組合框按鈕對齊到工具列頂部。

### <a name="remarks"></a>備註

默認情況下,組合框按鈕與頂部對齊。

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComBox按鈕::設定上下文選單ID

設置組合框按鈕的快捷功能表資源 ID。

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>參數

*uiResID*<br/>
[在]快捷功能表資源 ID。

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarCombox按鈕::設定下拉高度

下下列表框時設置其高度。

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
[在]清單框的高度(以像素為單位)。

### <a name="remarks"></a>備註

預設高度為 150 圖元。

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComBox按鈕::設定平模式

設置應用程式中組合框按鈕的平面樣式外觀。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
[在]對於平面樣式的外觀,TRUE;否則 FALSE。

### <a name="remarks"></a>備註

組合框按鈕的預設平面樣式為 FALSE。

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComBox按鈕::設定樣式

設置組合框按鈕的指定樣式,如果未禁用控制項,則重新繪製該控制項。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
[在]工具列樣式的位組合 (OR)。

### <a name="remarks"></a>備註

有關工具列按鈕樣式的清單,請參閱[工具列控制元件樣式](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComBox按鈕::設定文字

在組合框按鈕的編輯框中設定文本。

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[在]指向包含編輯框文字的字串的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CMFC工具列:更換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)

---
title: CMFCShellTreeCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 1fc422c3aca3efe1fb177e7a3567530d70c27119
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410057"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 類別

`CMFCShellTreeCtrl`類別會擴充[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)透過顯示 Shell 項目階層。

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。
## <a name="syntax"></a>語法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|傳回傳遞至的旗標的組合[IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|擷取項目的路徑。|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|將指標傳回至[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件，其可搭配這`CMFCShellTreeCtrl`物件來建立類似檔案總管的視窗。|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|此視窗的父視窗收到通知訊息，此視窗時，會呼叫此成員函式。 (覆寫[On_xxx_reflect](../../mfc/reference/cwnd-class.md#onchildnotify)。)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|重新整理，並重新繪製目前`CMFCShellTreeCtrl`物件。|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|選取適當的樹狀目錄控制項項目提供的 PIDL 或字串路徑為基礎。|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|設定旗標來篩選樹狀目錄的路徑 (類似於使用的旗標`IShellFolder::EnumObjects`)。|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|設定目前之間的關聯`CMFCShellTreeCtrl`物件和`CMFCShellListCtrl`物件。|

## <a name="remarks"></a>備註

此類別會擴充`CTreeCtrl`藉由啟用您的程式，包括 Windows Shell 項目，在樹狀目錄中的類別。 這個類別可以與相關聯`CMFCShellListCtrl`物件來建立完整的 [總管] 視窗。 然後，選取項目樹狀結構中將會顯示一份 Windows Shell 項目相關聯的清單。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>需求

**標頭：** afxshelltreeCtrl.h

## <a name="example"></a>範例

下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。 此程式碼片段是一部分[總管範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

可讓快顯功能表。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]布林值，指定是否要啟用快顯功能表。

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

傳回設定之旗標[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>傳回值

設定的 DWORD 值，指定目前的旗標的組合。

### <a name="remarks"></a>備註

在設定的旗標`CMFCShellTreeCtrl`傳送至方法[IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)每次重新整理物件。 您可以變更的旗標[CMFCShellTreeCtrl::SetFlags](#setflags)方法。

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

擷取的路徑中的項目[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
[out]字串參數的參考。 方法會將項目的路徑寫入此參數。

*htreeItem*<br/>
[in]方法會擷取此樹狀結構控制項項目的路徑。

### <a name="return-value"></a>傳回值

如果成功則為非零否則為 0。

### <a name="remarks"></a>備註

如果此方法失敗， *strPath*包含空字串。

如果您未指定*hTreeItem*，這個方法會嘗試取得目前選取項目的字串。 如果在不選取任何項目和*hTreeItem*是 NULL，這個方法會失敗。

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

將指標傳回至[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)與此相關聯的物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>傳回值

指標`CMFCShellListCtrl`與此樹狀結構控制項物件相關聯的物件。

### <a name="remarks"></a>備註

藉由使用`CMFCShellListCtrl`物件搭配`CMFCShellTreeCtrl`物件時，您可以建立類似檔案總管的視窗。 使用方法[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)建立關聯的兩個類別。 與其相關聯之後，架構會自動更新`CMFCShellListCtrl`如果中的選取範圍`CMFCShellTreeCtrl`變更。

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>參數

[in] *message*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
[in] *pLResult*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

[in] *pItem*<br/>
[in] *bSelected*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

[in] *pItem*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

重新整理，並重新繪製[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```
void Refresh();
```

### <a name="remarks"></a>備註

呼叫這個方法來重新整理中所顯示的項目階層架構`CMFCShellTreeCtrl`。

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

選取中的項目[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)根據提供的路徑。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
[in]字串，指定項目的路徑。

*lpidl*<br/>
[in]指定的項目 PIDL

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_FAIL。

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

設定旗標來篩選樹狀目錄的內容。

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
[in]若要設定旗標。

*bRefresh*<br/>
[in]布林值，指定是否`CMFCShellTreeCtrl`應該立即重新整理。

### <a name="remarks"></a>備註

`CMFCShellTreeCtrl`所有設定旗標為傳遞[IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。 不同的旗標之值的相關資訊，請參閱[IShellFolder::EnumObjects](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

將產生關聯[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件。

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>參數

*pShellList*<br/>
[in]指標`CMFCShellListCtrl`物件。

### <a name="remarks"></a>備註

這個方法產生關聯`CMFCShellListCtrl`與`CMFCShellTreeCtrl`。 這些物件可能會顯示為類似檔案總管的視窗： 如果使用者選取中的物件`CMFCShellTreeCtrl`，則關聯的項目中的`CMFCShellListCtrl`將會自動更新。

使用方法[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)來擷取`CMFCShellListCtrl`相關聯`CMFCShellTreeCtrl`。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)

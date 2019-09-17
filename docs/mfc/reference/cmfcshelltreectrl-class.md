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
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504915"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 類別

類別會藉由顯示 Shell 專案的階層來擴充[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)功能。 `CMFCShellTreeCtrl`

如需詳細資訊，請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。
## <a name="syntax"></a>語法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快捷方式功能表。|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|傳回傳遞至[IShellFolder：： EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)的旗標組合。|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|抓取專案的路徑。|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|傳回[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件的指標，這個物件與這個`CMFCShellTreeCtrl`物件一起使用，以建立類似 Explorer 的視窗。|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|此成員函式會在收到適用于此視窗的通知訊息時，由這個視窗的父視窗呼叫。 （覆寫[CWnd：： OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)。）|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|重新整理並重新繪製`CMFCShellTreeCtrl`目前的物件。|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|根據提供的 PIDL 或字串路徑，選取適當的樹狀目錄控制項專案。|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|設定旗標以篩選樹狀結構內容（類似于所使用`IShellFolder::EnumObjects`的旗標）。|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|設定目前`CMFCShellTreeCtrl`物件`CMFCShellListCtrl`和物件之間的關聯性。|

## <a name="remarks"></a>備註

此類別可讓`CTreeCtrl`您的程式在樹狀結構中包含 Windows Shell 專案，藉此擴充類別。 這個類別可以與`CMFCShellListCtrl`物件產生關聯，以建立完整的 Explorer 視窗。 然後，選取樹狀目錄中的專案，就會在相關聯的清單中顯示 Windows Shell 專案的清單。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>需求

**標頭：** afxshelltreeCtrl。h

## <a name="example"></a>範例

下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。 此程式碼片段是[Explorer 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellCoNtextMenu

啟用快捷方式功能表。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在布林值，指定是否要啟用快捷方式功能表。

##  <a name="getflags"></a>CMFCShellTreeCtrl：： GetFlags

傳回針對[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件所設定的旗標。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>傳回值

DWORD 值，指定目前設定的旗標組合。

### <a name="remarks"></a>備註

每當重新整理物件時`CMFCShellTreeCtrl` ，在中設定的旗標就會傳送至方法[IShellFolder：： EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) 。 您可以使用[CMFCShellTreeCtrl：： SetFlags](#setflags)方法來變更旗標。

##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

抓取[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)物件中專案的路徑。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
脫銷字串參數的參考。 方法會將專案的路徑寫入此參數。

*htreeItem*<br/>
在方法會抓取此樹狀目錄控制項專案的路徑。

### <a name="return-value"></a>傳回值

如果成功，則為非零;否則為0。

### <a name="remarks"></a>備註

如果此方法失敗， *strPath*會包含空字串。

如果您未指定*hTreeItem*，這個方法會嘗試取得目前所選取專案的字串。 如果未選取任何專案，且*hTreeItem*為 Null，則這個方法會失敗。

##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

傳回與這個[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件相關聯之[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件的指標。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>傳回值

與這個樹狀結構`CMFCShellListCtrl`控制項物件相關聯之物件的指標。

### <a name="remarks"></a>備註

藉由搭配`CMFCShellListCtrl` `CMFCShellTreeCtrl`物件使用物件，您可以建立類似 Explorer 的視窗。 使用[CMFCShellTreeCtrl：： SetRelatedList](#setrelatedlist)方法來建立兩個類別的關聯。 關聯之後， `CMFCShellListCtrl`如果`CMFCShellTreeCtrl`中的選取範圍變更，架構就會自動更新。

##  <a name="onchildnotify"></a>CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>參數

在*訊息*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
在*pLResult*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

[in] *pItem*<br/>
在*bSelected*<br/>

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

重新整理並重新繪製[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```
void Refresh();
```

### <a name="remarks"></a>備註

呼叫這個方法，以重新整理中`CMFCShellTreeCtrl`顯示之專案的階層。

##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

根據提供的路徑，在[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)中選取一個專案。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
在指定專案路徑的字串。

*lpidl*<br/>
在指定專案的 PIDL

### <a name="return-value"></a>傳回值

如果成功，則為 S_OK;否則為 E_FAIL。

##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

設定旗標以篩選樹狀結構內容。

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
在要設定的旗標。

*bRefresh*<br/>
在布林值，指定是否`CMFCShellTreeCtrl`應該立即重新整理。

### <a name="remarks"></a>備註

`CMFCShellTreeCtrl`會將所有設定旗標傳遞至[IShellFolder：：EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。 如需不同旗標值的詳細資訊，請參閱[IShellFolder：： EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。

##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

建立[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件與[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件的關聯。

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>參數

*pShellList*<br/>
在`CMFCShellListCtrl`物件的指標。

### <a name="remarks"></a>備註

這個方法會將`CMFCShellListCtrl` `CMFCShellTreeCtrl`與產生關聯。 這些物件可能會顯示為類似 Explorer 的視窗：如果使用者選取中`CMFCShellTreeCtrl`的物件， `CMFCShellListCtrl`中的相關專案將會自動更新。

使用方法[CMFCShellTreeCtrl：： GetRelatedList](#getrelatedlist)來抓取與`CMFCShellListCtrl` `CMFCShellTreeCtrl`相關聯的。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)

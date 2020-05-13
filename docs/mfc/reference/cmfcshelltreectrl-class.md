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
ms.openlocfilehash: c6f5856e92c2aca1d23ee6a37b99ea9700ea6db0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753437"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 類別

該`CMFCShellTreeCtrl`類通過顯示 Shell 項的層次結構來擴展[CTreeCtrl 類](../../mfc/reference/ctreectrl-class.md)功能。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCShellTreeCtrl::啟用ShellContextMenu](#enableshellcontextmenu)|啟用或禁用快捷功能表。|
|[CMFCShellTreeCtrl::獲取Flags](#getflags)|返回傳遞給[IShellFolder::enum 物件](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)的標誌組合。|
|[CMFCShellTreeCtrl:取得項目路徑](#getitempath)|檢索項的路徑。|
|[CMFCShellTreeCtrl:取得相關清單](#getrelatedlist)|返回指向[CMFCShellListCtrl 類](../../mfc/reference/cmfcshelllistctrl-class.md)物件的指標,該物件`CMFCShellTreeCtrl`與此 物件一起使用以創建類似資源管理器的視窗。|
|[CMFCShelltreectrl::在兒童通知](#onchildnotify)|當此視窗的父視窗收到應用於此視窗的通知消息時,此成員函數將調用它。 (覆蓋[Cwnd:onChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).)|
|[CMFCShelltreectrl:ongetItemicon](#ongetitemicon)||
|[CMFCShelltreectrl::在獲取項目文本](#ongetitemtext)||
|[CMFC舍爾特裡克::刷新](#refresh)|刷新並重新繪製當前`CMFCShellTreeCtrl`物件。|
|[CMFCShellTreeCtrl:選擇路徑](#selectpath)|根據提供的 PIDL 或字串路徑選擇適當的樹控件項。|
|[CMFCShellTreeCtrl::設置標誌](#setflags)|設置標誌以篩選樹上下文(類似於`IShellFolder::EnumObjects`使用的標誌)。|
|[CMFCShellTreeCtrl::設置相關清單](#setrelatedlist)|設置當前`CMFCShellTreeCtrl`物件`CMFCShellListCtrl`和 對象之間的關係。|

## <a name="remarks"></a>備註

此類通過使程式`CTreeCtrl`在樹中包括 Windows Shell 項來擴展類。 類可以與物件關聯以創建`CMFCShellListCtrl`完整的資源管理器視窗。 然後,在樹中選擇專案將在關聯的清單中顯示 Windows 殼項的清單。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>需求

**標題:** afxshelltreeCtrl.h

## <a name="example"></a>範例

下列範例示範如何建立 `CMFCShellTreeCtrl` 類別的物件。 此代碼段是[資源管理器範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::啟用ShellContextMenu

啟用快捷功能表。

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]指定是否啟用快捷選單的布林。

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl::獲取Flags

返回為[CMFCShellTreeCtrl 類](../../mfc/reference/cmfcshelltreectrl-class.md)物件設置的標誌。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>傳回值

指定目前設定的標誌組合的 DWORD 值。

### <a name="remarks"></a>備註

在 中設置的`CMFCShellTreeCtrl`標誌 將發送到方法[IShellFolder:::EnumObject,](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)每當刷新物件時。 您可以使用[CMFCShellTreeCtrl::setFlags](#setflags)方法更改標誌。

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl:取得項目路徑

檢索[CMFCShellTreeCtrl 類](../../mfc/reference/cmfcshelltreectrl-class.md)中項的路徑。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>參數

*斯特路徑*<br/>
[出]對字串參數的引用。 方法將項的路徑寫入此參數。

*htreeItem*<br/>
[在]該方法檢索此樹控件項的路徑。

### <a name="return-value"></a>傳回值

如果成功,則非零;0 否則。

### <a name="remarks"></a>備註

如果此方法失敗 *,strPath*包含空字串。

如果不指定*hTreeItem,* 此方法將嘗試取得目前選定項的字串。 如果未選擇任何項目,並且*hTreeItem*為 NULL,則此方法將失敗。

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl:取得相關清單

返回指向與此[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件關聯的[CMFCShellListCtrl 類](../../mfc/reference/cmfcshelllistctrl-class.md)物件的指標。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>傳回值

指向與此樹控件`CMFCShellListCtrl`物件關聯的物件的指標。

### <a name="remarks"></a>備註

通過將`CMFCShellListCtrl`物件與物件`CMFCShellTreeCtrl`結合 使用,可以創建類似於資源管理器的視窗。 使用方法[CMFCShellTreeCtrl::設置關聯列表](#setrelatedlist)來關聯這兩個類。 關聯後,框架會自動更新 更改`CMFCShellListCtrl``CMFCShellTreeCtrl`中的 「如果」。

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShelltreectrl::在兒童通知

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>參數

[在]*訊息*<br/>
[在]*wParam*<br/>
[在]*lParam*<br/>
[在]*pLResult*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShelltreectrl:ongetItemicon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

[在]*pItem*<br/>
[在]*b選定*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShelltreectrl::在獲取項目文本

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

[在]*pItem*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFC舍爾特裡克::刷新

刷新並重新繪製[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```cpp
void Refresh();
```

### <a name="remarks"></a>備註

呼叫此方法以刷新 中顯示的項目的層次`CMFCShellTreeCtrl`結構 。

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl:選擇路徑

根據提供的路徑選擇[CMFCShellTreeCtrl 類](../../mfc/reference/cmfcshelltreectrl-class.md)中的專案。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
[在]指定項目的字串。

*爾比德爾*<br/>
[在]指定項目的 PIDL

### <a name="return-value"></a>傳回值

S_OK如果成功;否則E_FAIL。

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl::設置標誌

設置標誌以篩選樹上下文。

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
[在]要設置的標誌。

*b 刷新*<br/>
[在]指定是否應立即刷新`CMFCShellTreeCtrl`的 布林。

### <a name="remarks"></a>備註

將所有`CMFCShellTreeCtrl`設定的標誌傳遞給[IShellfolder::枚舉物件](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。 有關不同標誌的值的詳細資訊,請參閱[IShellFolder::枚舉物件](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl::設置相關清單

將[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件與[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件關聯。

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>參數

*p殼清單*<br/>
[在]指向`CMFCShellListCtrl`物件的指標。

### <a name="remarks"></a>備註

此方法將`CMFCShellListCtrl`a`CMFCShellTreeCtrl`與 。 這些物件可以顯示為類似於資源管理員的視窗:如果使用者在 中選擇的`CMFCShellTreeCtrl`物件 ,`CMFCShellListCtrl`則中的關聯項將自動更新。

使用方法[CMFCShellTreeCtrl:獲取相關列表](#getrelatedlist)來檢`CMFCShellListCtrl`索與`CMFCShellTreeCtrl`關聯的 方法。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)

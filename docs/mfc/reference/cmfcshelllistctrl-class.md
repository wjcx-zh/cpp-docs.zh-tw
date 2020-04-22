---
title: CMFCShellListCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 445556535217b0887a02227a0773c287911922a2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753482"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 類別

該`CMFCShellListCtrl`類提供 Windows 清單控制項功能,並透過包括顯示 shell 項清單的功能來擴展它。

## <a name="syntax"></a>語法

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|顯示提供的資料夾中的項目清單。|
|[CMFCShellListCtrl::D播放父資料夾](#displayparentfolder)|顯示目前顯示的資料夾的父級資料夾中包含的專案清單。|
|[CMFCShellListCtrl::啟用ShellContextMenu](#enableshellcontextmenu)|啟用或禁用快捷功能表。|
|[CMFCShelllistCtrl::取得目前資料夾](#getcurrentfolder)|檢索當前資料夾的路徑。|
|[CMFCShelllistCtrl::取得目前的資料夾名稱](#getcurrentfoldername)|檢索當前資料夾的名稱。|
|[CMFCShelllistCtrl:取得目前的項目 Id 清單](#getcurrentitemidlist)|返回當前清單控制項的 PIDL。|
|[CMFCShelllistCtrl::獲取當前舍爾貝](#getcurrentshellfolder)|返回指向當前 Shell 資料夾的指標。|
|[CMFCShelllistCtrl:取得項目路徑](#getitempath)|返回項的文本路徑。|
|[CMFCShelllistCtrl:取得項目類型](#getitemtypes)|返回清單控制項顯示的 Shell 項類型。|
|[CMFCShelllistCtrl:是桌面](#isdesktop)|檢查目前選擇的資料夾是否為桌面資料夾。|
|[CMFCShelllistctrl::上比較專案](#oncompareitems)|框架在比較兩個專案時調用此方法。 (覆寫[CMFCListCtrl:在比較專案](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShelllistctrl:在格式檔案日期](#onformatfiledate)|當框架檢索清單控制項顯示的檔日期時調用。|
|[CMFCShelllistCtrl:在格式檔案大小](#onformatfilesize)|當框架轉換清單控制件的檔大小時調用。|
|[CMFCShelllistctrl:ongetItemicon](#ongetitemicon)|當框架檢索清單控件項的圖示時調用。|
|[CMFCShelllistctrl::在取得項目文字](#ongetitemtext)|當框架轉換清單控制項項的文本時呼叫。|
|[CMFCShelllistctrl::打開列](#onsetcolumns)|框架在設置列的名稱時調用它。|
|[CMFCShellListCtrl::刷新](#refresh)|刷新並重新繪製清單控制項。|
|[CMFCShelllistCtrl::設定項目類型](#setitemtypes)|設定清單控制項顯示的項目的類型。|

## <a name="remarks"></a>備註

該`CMFCShellListCtrl`類通過使程式能夠列出 Windows 外殼項來擴展[CMFCListCtrl 類](../../mfc/reference/cmfclistctrl-class.md)的功能。 使用的顯示格式類似於資源管理器視窗的清單檢視。

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件可以與物件關聯以`CMFCShellListCtrl`創建 完整的資源管理器視窗。 然後,在中選擇中的項`CMFCShellTreeCtrl`將`CMFCShellListCtrl`導致 物件列出所選項的內容。

## <a name="example"></a>範例

下面的範例展示如何建立`CMFCShellListCtrl`類的物件以及如何顯示當前顯示的資料夾的父資料夾。 此代碼段是[資源管理器範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>需求

**標題:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

顯示提供的資料夾中的項目清單。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
[在]包含資料夾路徑的字串。

*lpItemInfo*<br/>
[在]指向要顯示的`LPAFX_SHELLITEMINFO`資料夾的結構的指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則E_FAIL。

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::D播放父資料夾

更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件以顯示當前顯示的資料夾的父資料夾。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>傳回值

S_OK如果成功;否則E_FAIL。

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::啟用ShellContextMenu

啟用快捷功能表。

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]指定框架是否啟用快捷選單的布林。

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShelllistCtrl::取得目前資料夾

檢索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中當前選定資料夾的路徑。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>參數

*斯特路徑*<br/>
[出]對字串參數的引用,該方法在其中寫入路徑。

### <a name="return-value"></a>傳回值

如果成功,則非零;0 否則。

### <a name="remarks"></a>備註

如果在 中未選擇資料夾`CMFCShellListCtrl`, 則此方法將失敗。

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShelllistCtrl::取得目前的資料夾名稱

檢索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中目前選取的資料夾的名稱。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>參數

*strName*<br/>
[出]對字串參數的引用,該方法在其中寫入名稱。

### <a name="return-value"></a>傳回值

如果成功,則非零;0 否則。

### <a name="remarks"></a>備註

如果在 中未選擇資料夾`CMFCShellListCtrl`, 則此方法將失敗。

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShelllistCtrl:取得目前的項目 Id 清單

返回當前選定項的 PIDL。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>傳回值

當前項的 PIDL。

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShelllistCtrl::獲取當前舍爾貝

獲取指向[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中當前選定項的指標。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>傳回值

指向所選物件的[IShellFolder 介面](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder)的指標。

### <a name="remarks"></a>備註

如果目前未選擇任何物件,此方法將返回 NULL。

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShelllistCtrl:取得項目路徑

檢索項目的路徑。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>參數

*斯特路徑*<br/>
[出]對接收路徑的字串的引用。

*iItem*<br/>
[在]清單項的索引。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE;否則。

### <a name="remarks"></a>備註

*iItem*提供的索引基於[CMFCShellListCtrl 類](../../mfc/reference/cmfcshelllistctrl-class.md)物件當前顯示的專案。

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShelllistCtrl:取得項目類型

返回[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示的項目類型。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>傳回值

包含 中列出的項目類型的[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)值`CMFCShellListCtrl`。

### <a name="remarks"></a>備註

要設定`CMFCShellListCtrl`列出的項目類型,請執行式[CMFCShellListCtrl::設定項目類型](#setitemtypes)。

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShelllistCtrl:是桌面

確定[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中顯示的資料夾是否為桌面資料夾。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>傳回值

如果顯示的資料夾是桌面資料夾,則為 TRUE;如果顯示的資料夾是桌面資料夾,則為 TRUE。否則。

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShelllistctrl::上比較專案

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>參數

[在]*lParam1*<br/>
[在]*lParam2*<br/>
[在]*iColumn*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShelllistctrl:在格式檔案日期

當必須將與物件關聯的日期轉換為字串時,框架將調用此方法。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>參數

*tmFile*<br/>
[在]與文件關聯的日期。

*Str*<br/>
[出]包含格式化檔案日期的字串。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示與檔關聯的日期時,它必須將該日期轉換為字串格式。 `CMFCShellListCtrl`使用此方法進行該轉換。 預設情況下,此方法使用當前區域設置將日期格式化為字串。

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShelllistCtrl:在格式檔案大小

當框架將物件的大小轉換為字串時,它將調用此方法。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>參數

*l 檔案大小*<br/>
[在]框架將顯示的檔案的大小。

*Str*<br/>
[出]包含格式化檔案大小的字串。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類](../../mfc/reference/cmfcshelllistctrl-class.md)物件需要顯示檔的大小時,它需要將檔案大小轉換為字串格式。 `CMFCShellListCtrl`使用此方法進行該轉換。 預設情況下,此方法將檔大小從位元組轉換為千位元組,然後使用當前區域設置將大小格式化為字串。

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShelllistctrl:ongetItemicon

框架呼叫此方法以檢索與 shell 清單項關聯的圖示。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
[在]項索引。

*pItem*<br/>
[在]描述項的LPAFX_SHELLITEMINFO參數。

### <a name="return-value"></a>傳回值

圖示圖像的索引(如果成功);-1 如果函數失敗。

### <a name="remarks"></a>備註

圖示圖像索引基於系統映射清單。

預設情況下,此方法依賴於*pItem*參數。 在預設實現中不使用*iItem*的值。 您可以使用*iItem*實現自定義行為。

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShelllistctrl::在取得項目文字

當必須檢索 shell 項的文本時,框架將調用此方法。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
[在]項索引。

*iColumn*<br/>
[在]感興趣的列。

*pItem*<br/>
[在]描述項的LPAFX_SHELLITEMINFO參數。

### <a name="return-value"></a>傳回值

包含`CString`與項目關聯的文字的 。

### <a name="remarks"></a>備註

`CMFCShellListCtrl`物件中的每個項在一個或多個列中可能具有文本。 當框架調用此方法時,它指定它感興趣的列。 如果手動調用此函數,則還必須指定您感興趣的列。

預設情況下,此方法依賴於*pItem*參數來確定要處理的項。 在預設實現中不使用*iItem*的值。

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShelllistctrl::打開列

框架在設置列的名稱時調用此方法。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>備註

預設情況下,框架在物件中建立四欄`CMFCShellListCtrl`。 這些欄位名稱是**名稱**、**大小**、**類型**與**已變更**。 可以重寫此方法以自定義列數及其名稱。

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::刷新

刷新並重新繪製[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>傳回值

`S_OK`如果成功;否則是錯誤值。

### <a name="remarks"></a>備註

呼叫此方法以刷新`CMFCShellListCtrl`物件顯示的項目清單。

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShelllistCtrl::設定項目類型

設置[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中列出的項的類型。

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>參數

*n 類型*<br/>
[在]`CMFCShellListCtrl`物件支援的項類型的清單。

### <a name="remarks"></a>備註

關於項目類型清單的詳細資訊,請參閱[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)

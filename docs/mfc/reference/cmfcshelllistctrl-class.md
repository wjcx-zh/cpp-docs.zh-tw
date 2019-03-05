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
ms.openlocfilehash: a08cfff3996d3dce617cf80293a96675083a39d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302542"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 類別

`CMFCShellListCtrl`類別提供 Windows 清單控制項功能，並會將它展開加入顯示 shell 項目清單的能力。

## <a name="syntax"></a>語法

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|會顯示一份包含在提供的資料夾中的項目。|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|顯示目前所顯示資料夾的父資料夾中包含的項目清單。|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|擷取目前的資料夾路徑。|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|擷取目前的資料夾名稱。|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|傳回目前的清單控制項項目的 PIDL。|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|讓指標回到目前的殼層資料夾中。|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|傳回文字項目的路徑。|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|傳回清單控制項所顯示 Shell 項目類型。|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|檢查目前選取的資料夾是否為 [桌面] 資料夾。|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|它會比較兩個項目時，架構會呼叫這個方法。 (覆寫[CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|當架構擷取清單控制項所顯示的檔案日期時呼叫。|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|當架構將轉換的檔案大小的清單控制項時呼叫。|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|此架構會擷取清單控制項項目的圖示時呼叫。|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|當架構將轉換的文字清單控制項項目時呼叫。|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|它會設定資料行的名稱時，由架構呼叫。|
|[CMFCShellListCtrl::Refresh](#refresh)|重新整理並重新繪製該清單控制項。|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|設定清單控制項所顯示的項目的類型。|

## <a name="remarks"></a>備註

`CMFCShellListCtrl`類別會擴充功能[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)藉由啟用您的程式，列出 Windows shell 項目。 使用的顯示格式如下，檔案總管視窗的清單檢視。

A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)可以與物件相關聯`CMFCShellListCtrl`物件來建立完整的 [總管] 視窗。 然後，選取中的項目`CMFCShellTreeCtrl`會導致`CMFCShellListCtrl`列出選取的項目內容的物件。

## <a name="example"></a>範例

下列範例示範如何建立的物件`CMFCShellListCtrl`類別以及如何顯示目前所顯示資料夾的上層資料夾。 此程式碼片段是一部分[總管範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>需求

**標頭：** afxshelllistCtrl.h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

會顯示一份包含在提供的資料夾中的項目。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
[in]包含的資料夾路徑的字串。

*lpItemInfo*<br/>
[in]指標`LPAFX_SHELLITEMINFO`結構，描述要顯示的資料夾。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_FAIL。

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件，以顯示目前所顯示資料夾的上層資料夾。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則 E_FAIL。

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

可讓快顯功能表。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]布林值，指定架構是否啟用快顯功能表。

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

擷取目前選取的資料夾中的路徑[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
[out]其中方法會將路徑字串參數的參考。

### <a name="return-value"></a>傳回值

如果成功則為非零否則為 0。

### <a name="remarks"></a>備註

這個方法會失敗，如果有任何資料夾中選取`CMFCShellListCtrl`。

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

擷取目前選取的資料夾中的名稱[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>參數

*strName*<br/>
[out]其中的方法，將名稱寫入字串參數的參考。

### <a name="return-value"></a>傳回值

如果成功則為非零否則為 0。

### <a name="remarks"></a>備註

這個方法會失敗，如果有任何資料夾中選取`CMFCShellListCtrl`。

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

傳回目前所選項目的 PIDL。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>傳回值

目前項目的 PIDL。

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

取得在目前選取的項目指標[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>傳回值

指標[IShellFolder 介面](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ishellfolder)針對選取的物件。

### <a name="remarks"></a>備註

如果目前沒有選取任何物件，這個方法會傳回 NULL。

##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath

擷取項目的路徑。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
[out]接收路徑字串的參考。

*iItem*<br/>
[in]清單項目的索引。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUEFALSE 否則。

### <a name="remarks"></a>備註

所提供的索引*iItem*根據目前所顯示的項目[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes

傳回顯示的項目型別[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>傳回值

A [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf)值，其中包含的項目中所列類型`CMFCShellListCtrl`。

### <a name="remarks"></a>備註

若要設定中所列的項目類型`CMFCShellListCtrl`，呼叫[CMFCShellListCtrl::SetItemTypes](#setitemtypes)。

##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop

如果資料夾，就是會決定顯示在[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件是 [桌面] 資料夾。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>傳回值

如果顯示的資料夾是 [桌面] 資料夾中;，則為 TRUE。FALSE 否則。

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>參數

[in] *lParam1*<br/>
[in] *lParam2*<br/>
[in] *iColumn*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

當它必須轉換成字串，與物件相關聯的日期時，架構會呼叫這個方法。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>參數

*tmFile*<br/>
[in]與檔案關聯的日期。

*str*<br/>
[out]字串，包含格式的檔案的日期。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示與檔案相關聯的日期，它必須將該日期轉換成字串格式。 `CMFCShellListCtrl`讓該轉換會使用這個方法。 根據預設，此方法會使用目前的地區設定日期格式轉換為字串。

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

將物件大小轉換成字串時，架構會呼叫這個方法。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>參數

*lFileSize*<br/>
[in]此架構會顯示檔案的大小。

*str*<br/>
[out]字串，包含格式的檔案大小。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件需要顯示檔案的大小，它必須轉換成字串格式的檔案大小。 `CMFCShellListCtrl`讓該轉換會使用這個方法。 根據預設，這個方法會從位元組轉換檔案的大小，以 kb 為單位，然後使用目前的地區設定格式化字串的大小。

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

架構會呼叫這個方法來擷取 shell 清單項目相關聯的圖示。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
[in]項目索引。

*pItem*<br/>
[in]LPAFX_SHELLITEMINFO 參數描述項目。

### <a name="return-value"></a>傳回值

如果成功則圖示影像的索引在函數失敗時，為-1。

### <a name="remarks"></a>備註

圖示的影像索引為基礎的系統映像清單。

根據預設，此方法需仰賴*pItem*參數。 值*iItem*不會用於預設實作。 您可以使用*iItem*來實作自訂行為。

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

它必須擷取 shell 項目的文字時，架構會呼叫這個方法。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
[in]項目索引。

*iColumn*<br/>
[in]感興趣的資料行。

*pItem*<br/>
[in]LPAFX_SHELLITEMINFO 參數描述項目。

### <a name="return-value"></a>傳回值

A`CString`其中包含項目相關聯的文字。

### <a name="remarks"></a>備註

在每個項目`CMFCShellListCtrl`物件可能有一或多個資料行中的文字。 架構會呼叫這個方法，它會指定它感興趣的資料行。 如果您以手動方式呼叫此函式，您也必須指定您感興趣的資料行。

根據預設，此方法需仰賴*pItem*參數，來判斷其項目程序。 值*iItem*不會用於預設實作。

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

它會設定資料行的名稱時，架構會呼叫這個方法。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>備註

根據預設，此架構會建立四個資料行中的`CMFCShellListCtrl`物件。 這些資料行的名稱是**名稱**，**大小**，**型別**，以及**Modified**。 您可以覆寫這個方法以自訂資料行和其名稱的數目。

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

重新整理，並重新繪製[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>傳回值

`S_OK` 如果登錄成功。，否則為錯誤值。

### <a name="remarks"></a>備註

呼叫這個方法來重新整理顯示的項目清單`CMFCShellListCtrl`物件。

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

設定項目中所列的型別[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>參數

*nTypes*<br/>
[in]清單項目的型別`CMFCShellListCtrl`物件支援。

### <a name="remarks"></a>備註

如需詳細的項目類型清單的相關資訊，請參閱[SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)

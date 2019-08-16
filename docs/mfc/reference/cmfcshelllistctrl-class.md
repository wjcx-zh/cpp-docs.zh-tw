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
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504927"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 類別

`CMFCShellListCtrl`類別提供了 Windows 清單控制項功能, 並藉由包含顯示 shell 專案清單的功能來加以擴充。

## <a name="syntax"></a>語法

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|顯示包含在所提供資料夾中的專案清單。|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|顯示資料夾中所包含的專案清單, 該資料夾為目前所顯示資料夾的父系。|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快捷方式功能表。|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|抓取目前資料夾的路徑。|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|抓取目前資料夾的名稱。|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|傳回目前清單控制項專案的 PIDL。|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|傳回目前 Shell 資料夾的指標。|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|傳回專案的文字路徑。|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|傳回清單控制項所顯示的 Shell 專案類型。|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|檢查目前選取的資料夾是否為 [桌面] 資料夾。|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|架構會在比較兩個專案時呼叫這個方法。 (覆寫[CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|當架構捕獲清單控制項所顯示的檔案日期時呼叫。|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|當架構轉換清單控制項的檔案大小時呼叫。|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|當架構捕獲清單控制項專案的圖示時呼叫。|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|當架構轉換清單控制項專案的文字時呼叫。|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|在設定資料行名稱時由架構呼叫。|
|[CMFCShellListCtrl::Refresh](#refresh)|重新整理並重新繪製清單控制項。|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|設定清單控制項所顯示的專案類型。|

## <a name="remarks"></a>備註

類別可讓您的程式列出 Windows shell 專案, 藉此擴充[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)的功能。 `CMFCShellListCtrl` 所使用的顯示格式與 [Explorer] 視窗的清單視圖類似。

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件可以與`CMFCShellListCtrl`物件產生關聯, 以建立完整的 Explorer 視窗。 然後, 在中`CMFCShellTreeCtrl`選取專案, 會`CMFCShellListCtrl`導致物件列出所選取專案的內容。

## <a name="example"></a>範例

下列範例示範如何建立`CMFCShellListCtrl`類別的物件, 以及如何顯示目前顯示之資料夾的父資料夾。 此程式碼片段是[Explorer 範例](../../overview/visual-cpp-samples.md)的一部分。

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

**標頭:** afxshelllistCtrl。h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

顯示包含在所提供資料夾中的專案清單。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
在包含資料夾路徑的字串。

*lpItemInfo*<br/>
在`LPAFX_SHELLITEMINFO`結構的指標, 描述要顯示的資料夾。

### <a name="return-value"></a>傳回值

如果成功, 則為 S_OK;否則為 E_FAIL。

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件, 以顯示目前顯示之資料夾的父資料夾。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>傳回值

如果成功, 則為 S_OK;否則為 E_FAIL。

##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellCoNtextMenu

啟用快捷方式功能表。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在布林值, 指定架構是否啟用快捷方式功能表。

##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

抓取[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中目前選取之資料夾的路徑。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
脫銷字串參數的參考, 其中方法會寫入路徑。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果中`CMFCShellListCtrl`沒有選取任何資料夾, 這個方法就會失敗。

##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

抓取[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中目前選取之資料夾的名稱。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>參數

*strName*<br/>
脫銷字串參數的參考, 其中方法會寫入名稱。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果中`CMFCShellListCtrl`沒有選取任何資料夾, 這個方法就會失敗。

##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

傳回目前所選取專案的 PIDL。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>傳回值

目前專案的 PIDL。

##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

取得[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中目前所選取專案的指標。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>傳回值

所選取物件之[IShellFolder 介面](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder)的指標。

### <a name="remarks"></a>備註

如果目前未選取任何物件, 這個方法會傳回 Null。

##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

抓取專案的路徑。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>參數

*strPath*<br/>
脫銷接收路徑之字串的參考。

*iItem*<br/>
在清單專案的索引。

### <a name="return-value"></a>傳回值

如果成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

*IItem*提供的索引是以[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件目前所顯示的專案為基礎。

##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

傳回[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件所顯示的專案類型。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>傳回值

[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)值, 其中包含中`CMFCShellListCtrl`列出的專案類型。

### <a name="remarks"></a>備註

若要設定中`CMFCShellListCtrl`所列的專案類型, 請呼叫[CMFCShellListCtrl:: SetItemTypes](#setitemtypes)。

##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

判斷[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中所顯示的資料夾是否為 [桌面] 資料夾。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>傳回值

如果顯示的資料夾是桌面資料夾, 則為 TRUE;否則為 FALSE。

##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>參數

[in] *lParam1*<br/>
[in] *lParam2*<br/>
在*iColumn*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

當此架構必須將與物件相關聯的日期轉換成字串時, 就會呼叫這個方法。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>參數

*tmFile*<br/>
在與檔案相關聯的日期。

*str*<br/>
脫銷包含已格式化之檔案日期的字串。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示與檔案相關聯的日期時, 它必須將該日期轉換成字串格式。 會`CMFCShellListCtrl`使用這個方法來進行轉換。 根據預設, 這個方法會使用目前的地區設定, 將日期格式化為字串。

##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

架構會在將物件的大小轉換成字串時呼叫這個方法。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>參數

*lFileSize*<br/>
在架構將顯示的檔案大小。

*str*<br/>
脫銷包含已格式化檔案大小的字串。

### <a name="remarks"></a>備註

當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件需要顯示檔案的大小時, 它需要將檔案大小轉換成字串格式。 會`CMFCShellListCtrl`使用這個方法來進行轉換。 根據預設, 這個方法會將檔案大小從位元組轉換成 kb, 然後使用目前的地區設定, 將大小格式化為字串。

##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

架構會呼叫這個方法來抓取與 shell 清單專案相關聯的圖示。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
在專案索引。

*pItem*<br/>
在描述專案的 LPAFX_SHELLITEMINFO 參數。

### <a name="return-value"></a>傳回值

如果成功, 則為圖示影像的索引;如果函數失敗, 則為-1。

### <a name="remarks"></a>備註

圖示影像索引是以系統影像清單為基礎。

根據預設, 這個方法會依賴*pItem*參數。 預設的執行中不會使用*iItem*的值。 您可以使用*iItem*來執行自訂行為。

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

當架構必須抓取 shell 專案的文字時, 會呼叫這個方法。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>參數

*iItem*<br/>
在專案索引。

*iColumn*<br/>
在感對的資料行。

*pItem*<br/>
在描述專案的 LPAFX_SHELLITEMINFO 參數。

### <a name="return-value"></a>傳回值

`CString` , 其中包含與專案相關聯的文字。

### <a name="remarks"></a>備註

物件中的`CMFCShellListCtrl`每個專案可能會有一或多個資料行中的文字。 當架構呼叫這個方法時, 它會指定其感興趣的資料行。 如果您以手動方式呼叫此函式, 您也必須指定您感興趣的資料行。

根據預設, 這個方法會依賴*pItem*參數來決定要處理的專案。 預設的執行中不會使用*iItem*的值。

##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

架構會在設定資料行的名稱時呼叫這個方法。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>備註

根據預設, 架構會在`CMFCShellListCtrl`物件中建立四個數據行。 這些資料行的名稱包括 [**名稱**]、[**大小**]、[**類型**] 和 [**已修改**]。 您可以覆寫這個方法, 以自訂資料行和其名稱的數目。

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

重新整理並重新繪製[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>傳回值

`S_OK`如果成功, 則為,否則為錯誤值。

### <a name="remarks"></a>備註

呼叫這個方法, 以重新整理`CMFCShellListCtrl`物件所顯示的專案清單。

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

設定[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件中列出的專案類型。

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>參數

*nTypes*<br/>
在`CMFCShellListCtrl`物件支援的專案類型清單。

### <a name="remarks"></a>備註

如需專案類型清單的詳細資訊, 請參閱[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)

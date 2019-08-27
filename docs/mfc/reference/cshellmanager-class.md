---
title: CShellManager 類別
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 8151550dafdd1bdf8593d555008af387cf548bc8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502626"
---
# <a name="cshellmanager-class"></a>CShellManager 類別

實作數個可讓您使用識別項清單指標 (PIDL) 的方法。

## <a name="syntax"></a>語法

```
class CShellManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|建構 `CShellManager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|顯示可讓使用者選取 shell 資料夾的對話方塊。|
|[CShellManager::ConcatenateItem](#concatenateitem)|串連兩個 Pidl。|
|[CShellManager::CopyItem](#copyitem)|建立新的 PIDL, 並將提供的 PIDL 複製到其中。|
|[CShellManager::CreateItem](#createitem)|建立指定之大小的新 PIDL。|
|[CShellManager::FreeItem](#freeitem)|刪除提供的 PIDL。|
|[CShellManager::GetItemCount](#getitemcount)|傳回所提供 PIDL 中的專案數。|
|[CShellManager::GetItemSize](#getitemsize)|傳回所提供之 PIDL 的大小。|
|[CShellManager::GetNextItem](#getnextitem)|傳回 PIDL 中的下一個專案。|
|[CShellManager::GetParentItem](#getparentitem)|抓取所提供專案的父專案。|
|[CShellManager::ItemFromPath](#itemfrompath)|抓取提供的路徑所識別之專案的 PIDL。|

## <a name="remarks"></a>備註

`CShellManager`類別的方法全都會處理 pidl。 PIDL 是 shell 物件的唯一識別碼。

您不應該手動建立`CShellManager`物件。 應用程式的架構會自動建立此檔案。 不過, 您應該在應用程式的初始化過程中呼叫[CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) 。 若要取得應用程式之 shell 管理員的指標, 請呼叫[CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>需求

**標頭:** afxshellmanager。h

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

顯示可讓使用者選取 shell 資料夾的對話方塊。

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>參數

*strOutFolder*<br/>
脫銷方法用來儲存所選資料夾路徑的字串。

*pWndParent*<br/>
在父視窗的指標。

*lplszInitialFolder*<br/>
在字串, 其中包含對話方塊顯示時預設選取的資料夾。

*lpszTitle*<br/>
在對話方塊的標題。

*ulFlags*<br/>
在指定對話方塊選項的旗標。 如需詳細描述, 請參閱[BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) 。

*piFolderImage*<br/>
脫銷整數值的指標, 此方法會在其中寫入所選資料夾的影像索引。

### <a name="return-value"></a>傳回值

如果使用者從對話方塊中選取資料夾, 則為非零值;否則為0。

### <a name="remarks"></a>備註

當您呼叫這個方法時, 應用程式會建立並顯示一個對話方塊, 讓使用者選取資料夾。 方法會將資料夾的路徑寫入*strOutFolder*參數。

### <a name="example"></a>範例

下列範例示範如何`CShellManager` `CWinAppEx::GetShellManager`使用方法`BrowseForFolder` , 以及如何使用方法, 來抓取物件的參考。 此程式碼片段是[Explorer 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem

建立包含兩個 Pidl 的新清單。

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>參數

*pidl1*<br/>
在第一個專案。

*pidl2*<br/>
在第二個專案。

### <a name="return-value"></a>傳回值

如果函式成功, 則為新專案清單的指標, 否則為 Null。

### <a name="remarks"></a>備註

這個方法會建立夠大的新[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) , 以同時包含*pidl1*和*pidl2*。 然後, 它會將*pidl1*和*pidl2*複製到新的清單。

##  <a name="copyitem"></a>CShellManager:: CopyItem

複製專案清單。

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>參數

*pidlSource*<br/>
在原始專案清單。

### <a name="return-value"></a>傳回值

如果成功, 則為新建立之專案清單的指標;否則為 Null。

### <a name="remarks"></a>備註

新建立的專案清單與來源專案清單的大小相同。

##  <a name="createitem"></a>CShellManager:: CreateItem

建立新的 PIDL。

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>參數

*cbSize*<br/>
在專案清單的大小。

### <a name="return-value"></a>傳回值

如果成功, 則為所建立專案清單的指標;否則為 Null。

##  <a name="cshellmanager"></a>CShellManager::CShellManager

建構 `CShellManager` 物件。

```
CShellManager();
```

### <a name="remarks"></a>備註

在大部分的情況下, 您不需要`CShellManager`直接建立。 根據預設, 架構會為您建立一個。 若要取得的`CShellManager`指標, 請呼叫[CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果您`CShellManager`手動建立, 則必須使用[CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)方法將它初始化。

##  <a name="freeitem"></a>CShellManager::FreeItem

刪除專案清單。

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*pidl*<br/>
在要刪除的專案清單。

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

傳回專案清單中的專案數。

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*pidl*<br/>
在專案清單的指標。

### <a name="return-value"></a>傳回值

專案清單中的專案數。

##  <a name="getitemsize"></a>CShellManager::GetItemSize

傳回專案清單的大小。

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*pidl*<br/>
在專案清單的指標。

### <a name="return-value"></a>傳回值

專案清單的大小。

##  <a name="getnextitem"></a>CShellManager:: GetNextItem

從專案識別碼清單 (PIDL) 的指標抓取下一個專案。

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*pidl*<br/>
在要逐一查看的專案清單。

### <a name="return-value"></a>傳回值

清單中下一個專案的指標。

### <a name="remarks"></a>備註

如果清單中沒有其他專案, 則這個方法會傳回 Null。

##  <a name="getparentitem"></a>CShellManager:: GetParentItem

抓取專案識別碼清單 (PIDL) 之指標的父系。

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>參數

*lpidl*<br/>
在將抓取其父系的 PIDL。

*lpidlParent*<br/>
脫銷PIDL 的參考, 其中方法會儲存結果。

### <a name="return-value"></a>傳回值

父 PIDL 的層級。

### <a name="remarks"></a>備註

PIDL 的層級相對於桌面。 桌面 PIDL 會被視為層級為0。

##  <a name="itemfrompath"></a>CShellManager::ItemFromPath

從字串路徑所識別的專案, 抓取專案識別碼清單 (PIDL) 的指標。

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
在指定專案路徑的字串。

*pidl*<br/>
脫銷PIDL 的參考。 方法會使用此 PIDL 來儲存其傳回值的指標。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 AAD-USERREADUSINGALTERNATIVESECURITYID-NOERROR;OLE 定義的錯誤值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)

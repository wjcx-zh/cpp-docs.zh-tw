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
ms.openlocfilehash: cc8aa9216fd0d4dcc169830fb745134ceb5c65fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318408"
---
# <a name="cshellmanager-class"></a>CShellManager 類別

實作數個可讓您使用識別項清單指標 (PIDL) 的方法。

## <a name="syntax"></a>語法

```
class CShellManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C殼管理員:C殼管理員](#cshellmanager)|建構 `CShellManager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CShell 管理員::瀏覽資料夾](#browseforfolder)|顯示一個對話框,使用戶能夠選擇 shell 資料夾。|
|[CShellManager:串聯專案](#concatenateitem)|連接兩個 PidL。|
|[C殼管理員:複製項目](#copyitem)|建立新的 PIDL 並將隨附的 PIDL 複製到它。|
|[CShell 管理員:建立項目](#createitem)|建立指定大小的新 PIDL。|
|[CShellManager:免費專案](#freeitem)|刪除提供的 PIDL。|
|[CShell 管理員:抓取項目計數](#getitemcount)|傳回提供的 PIDL 中的項目。|
|[CShell 管理員:抓取項目大小](#getitemsize)|傳回提供的 PIDL 的大小。|
|[CShellManager:取得下一個專案](#getnextitem)|從 PIDL 返回下一個項。|
|[CShellManager:取得父項](#getparentitem)|檢索提供的項的父項。|
|[CShell 管理員:專案從路徑](#itemfrompath)|檢索提供路徑標識的項的 PIDL。|

## <a name="remarks"></a>備註

`CShellManager`類的方法都處理 L。 PIDL 是 shell 物件的唯一識別碼。

不應手動創建`CShellManager`物件。 它將由應用程式的框架自動創建。 但是,您應該在應用程式的初始化過程中調用[CWinAppEx::在](../../mfc/reference/cwinappex-class.md#initshellmanager)應用程式的初始化過程中調用 ItShellManager。 要取得指向應用程式的 shell 管理員的指標,請致電[CWinAppEx::getShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>需求

**標題:** afxshell管理員.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShell 管理員::瀏覽資料夾

顯示一個對話框,使用戶能夠選擇 shell 資料夾。

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

*斯特魯特資料夾*<br/>
[出]用於儲存選取的資料夾的路徑的方法使用的字串。

*pwnd 父級*<br/>
[在]指向父視窗的指標。

*lplsz 初始資料夾*<br/>
[在]包含預設情況下顯示對話框時選擇的資料夾的字串。

*lpszTitle*<br/>
[在]對話框的標題。

*ulFlags*<br/>
[在]標記指定對話框的選項。 有關詳細說明,請參閱[BROWSEINFO。](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow)

*皮皮資料夾影像*<br/>
[出]指向整數值的指標,該方法在其中寫入所選資料夾的圖像索引。

### <a name="return-value"></a>傳回值

如果用戶從對話框中選擇資料夾,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫此方法時,應用程式將創建並顯示一個對話框,使用戶能夠選擇資料夾。 該方法將資料夾的路徑寫入*strOutFolder*參數。

### <a name="example"></a>範例

下面的範例展示如何使用`CShellManager``CWinAppEx::GetShellManager`方法檢索對物件的引用以及如何使用方法`BrowseForFolder`。 此代碼段是[資源管理器範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager:串聯專案

建立包含兩個 PidL 的新清單。

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>參數

*皮德爾1*<br/>
[在]第一個專案。

*皮德爾2*<br/>
[在]第二個專案。

### <a name="return-value"></a>傳回值

如果函數成功,則指向新專案列表的指標,否則為 NULL。

### <a name="remarks"></a>備註

此方法建立新的[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)大到足以包含*pidl1*與*pidl2*。 然後,它將*pidl1*和*pidl2*複製到新清單中。

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>C殼管理員:複製項目

複製項目清單。

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>參數

*皮德爾來源*<br/>
[在]原始項清單。

### <a name="return-value"></a>傳回值

指向新創建的項清單的指標(如果成功);否則 NULL。

### <a name="remarks"></a>備註

新創建的項目清單的大小與源項清單的大小相同。

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShell 管理員:建立項目

創建新的 PIDL。

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>參數

*cbSize*<br/>
[在]項清單的大小。

### <a name="return-value"></a>傳回值

如果成功,指向已創建項列表的指標;否則 NULL。

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>C殼管理員:C殼管理員

建構 `CShellManager` 物件。

```
CShellManager();
```

### <a name="remarks"></a>備註

在大多數情況下,您不必直接創建`CShellManager`。 默認情況下,框架會為您創建一個。 要取得指向的`CShellManager`指標,請致電[CWinAppEx::取得 ShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果手動創建一個`CShellManager`,則必須使用[CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)的方法初始化它。

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager:免費專案

刪除項目清單。

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*皮德爾*<br/>
[在]要刪除的項目清單。

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShell 管理員:抓取項目計數

傳回項目清單中的項目數。

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*皮德爾*<br/>
[在]指向項清單的指標。

### <a name="return-value"></a>傳回值

項清單中的項目數。

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShell 管理員:抓取項目大小

返回項目清單的大小。

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*皮德爾*<br/>
[在]指向項清單的指標。

### <a name="return-value"></a>傳回值

項清單的大小。

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager:取得下一個專案

從指向項識別碼清單 (PIDL) 的指標檢索下一個項。

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*皮德爾*<br/>
[在]要反覆運算的項目清單。

### <a name="return-value"></a>傳回值

指向清單中下一個專案的指標。

### <a name="remarks"></a>備註

如果清單中沒有更多的項,此方法將傳回 NULL。

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager:取得父項

檢索指向項識別碼清單 (PIDL) 的指標的父級。

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>參數

*爾比德爾*<br/>
[在]將檢索其父項的 PIDL。

*lpidl 家長*<br/>
[出]對 PIDL 的引用,該方法將在其中存儲結果。

### <a name="return-value"></a>傳回值

父 PIDL 的級別。

### <a name="remarks"></a>備註

PIDL 的級別與桌面相關。 桌面 PIDL 被視為具有 0 的級別。

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShell 管理員:專案從路徑

從字串路徑標識的項中檢索指向項標識符列表 (PIDL) 的指標。

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>參數

*lpszPath*<br/>
[在]指定項目的字串。

*皮德爾*<br/>
[出]對 PIDL 的引用。 該方法使用此 PIDL 儲存指向其返回值的指標。

### <a name="return-value"></a>傳回值

如果成功,返回 NOERROR;OLE 定義的錯誤值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)

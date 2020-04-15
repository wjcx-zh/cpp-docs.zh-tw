---
title: CRecentFileList 類別
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370900"
---
# <a name="crecentfilelist-class"></a>CRecentFileList 類別

支援最近使用的 (MRU) 檔案清單控制項。

## <a name="syntax"></a>語法

```
class CRecentFileList
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[最新檔案清單:"最新檔案清單"](#crecentfilelist)|建構 `CRecentFileList` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[最新的檔案清單::新增](#add)|將檔案加入 MRU 檔案清單。|
|[最新檔案清單:取得顯示名稱](#getdisplayname)|為 MRU 檔名的功能表顯示提供顯示名稱。|
|[最新檔案清單:取得 Size](#getsize)|檢索 MRU 檔案清單中的檔案數。|
|[最新檔案清單:閱讀清單](#readlist)|從註冊表或 讀取 MRU 檔案清單。INI 檔。|
|[最新檔案清單:刪除](#remove)|從 MRU 檔案清單中刪除檔案。|
|[最新檔案清單:更新選單](#updatemenu)|更新 MRU 檔案清單的功能表顯示。|
|[最新檔案清單:寫入清單](#writelist)|從註冊表或 寫入 MRU 檔案清單。INI 檔。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[最新檔案清單:運算子\[\]](#operator_at)|返回`CString`給定位置的物件。|

## <a name="remarks"></a>備註

檔案可以新增到 MRU 檔案清單中或從中移除,檔案清單可以從註冊表或 寫入 註冊表或 。可以更新 INI 檔案,並可以更新顯示 MRU 檔案清單的功能表。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CRecentFileList`

## <a name="requirements"></a>需求

**標題:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>最新的檔案清單::新增

將檔案加入最近使用的 (MRU) 檔案清單中。

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>參數

*lpszPath名稱*<br/>
指定要加入清單中的路徑名稱。

*lpszAppID*<br/>
為應用程式指定應用程式使用者型號 ID。

*pItem*<br/>
指定要加入清單中的指向殼項的指標。

*p 連結*<br/>
指定要加入清單中的指向 Shell 連結的指標。

*皮德爾*<br/>
指定要加入最近文件資料夾的 shell 的 IDLIST。

### <a name="remarks"></a>備註

文件名將添加到 MRU 列表的頂部。 如果 MRU 清單中已存在檔名,它將移動到頂部。

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>最新檔案清單:"最新檔案清單"

建構 `CRecentFileList` 物件。

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>參數

*N 開始*<br/>
MRU(最近使用)檔案清單的功能表顯示中編號的偏移量。

*lpsz節*<br/>
指向註冊表或應用程式的 部分的名稱。讀取和/或寫入 MRU 檔案清單的 INI 檔案。

*lpszentry格式*<br/>
指向用於存儲在註冊表或應用程式中的條目的名稱的格式字串。INI 檔。

*nSize*<br/>
MRU 檔案清單中的檔案的最大數量。

*nMaxDispLen*<br/>
MRU 檔案清單中的檔案名的功能表顯示的最大長度(以字元表示)。

### <a name="remarks"></a>備註

*lpszEntryFormat*指向的格式字串應包含"%d",用於替換每個 MRU 項的索引。 例如,如果格式字串是`"file%d"`,則條目將命名為`file0``file1`、 等。

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>最新檔案清單:取得顯示名稱

取得 MRU 檔案清單中檔案的顯示名稱,用於 MRU 清單的選單顯示。

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>參數

*strName*<br/>
其名稱將顯示在 MRU 檔案的選單清單中的檔案的完整路徑。

*nIndex*<br/>
MRU 檔案清單中檔案的基於零的索引。

*lpszCurdir*<br/>
儲存目前的目錄的字串。

*nCurDir*<br/>
當前目錄字串的長度。

*b 最小名稱*<br/>
如果非零,則指示應返回檔的基本名稱,即使它超過最大顯示長度(作為*nMaxDispLen*參數`CRecentFileList`傳遞給 構造函數)。

### <a name="return-value"></a>傳回值

如果最近使用的 (MRU) 檔案清單中的指定索引中沒有檔名,**則 FALSE。**

### <a name="remarks"></a>備註

如果文件位於當前目錄中,則函數將目錄從顯示幕上保留。 如果檔名太長,目錄和擴展名將被刪除。 如果檔名仍然太長,則顯示名稱將設置為空字串,除非*bAtLeastName*是非零。

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>最新檔案清單:取得 Size

檢索 MRU 檔案清單中的檔案數。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

目前最近使用 (MRU) 檔案清單中的檔案數。

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>C 最新檔案清單:運算符 |

重載子標(`[]`) 運算符`CString`傳回*由 nIndex*中的零基索引指定的單個。

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
s`CString``CString`的 零基索引。

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>最新檔案清單:閱讀清單

從註冊表或應用程式的 讀取最近使用 (MRU) 檔案清單。INI 檔。

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>最新檔案清單:刪除

從 MRU 檔案清單中刪除檔案。

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要從最近使用的 (MRU) 檔案清單中刪除的檔案的基於零的索引。

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>最新檔案清單:更新選單

更新 MRU 檔案清單的功能表顯示。

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標,用於最近使用 (MRU) 檔案清單功能表。

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>最新檔案清單:寫入清單

將最近使用的 (MRU) 檔案清單寫入註冊表或應用程式的 。INI 檔。

```
virtual void WriteList();
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)

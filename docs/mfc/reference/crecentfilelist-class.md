---
title: CRecentFileList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f8f3d1b4be06caeacc86718eafed432979b0c59
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069421"
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
|[CRecentFileList::CRecentFileList](#crecentfilelist)|建構 `CRecentFileList` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecentFileList::Add](#add)|將檔案加入至最近使用的檔案清單。|
|[CRecentFileList::GetDisplayName](#getdisplayname)|提供功能表顯示最近使用檔案名稱的顯示名稱。|
|[CRecentFileList::GetSize](#getsize)|擷取 MRU 檔案清單中的檔案的數目。|
|[CRecentFileList::ReadList](#readlist)|從登錄中讀取的最近使用的檔案清單或。INI 檔案。|
|[CRecentFileList::Remove](#remove)|從最近使用的檔案清單移除檔案。|
|[CRecentFileList::UpdateMenu](#updatemenu)|更新的功能表顯示的 MRU 檔案清單。|
|[CRecentFileList::WriteList](#writelist)|從登錄寫入 MRU 檔案清單或。INI 檔案。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CRecentFileList::operator]](#operator_at)|傳回`CString`物件中指定的位置。|

## <a name="remarks"></a>備註

檔案可以加入或刪除從最近使用的檔案清單，可讀取或寫入登錄的檔案清單或。可以更新 INI 檔，並顯示最近使用的檔案清單的功能表。

## <a name="inheritance-hierarchy"></a>繼承階層

`CRecentFileList`

## <a name="requirements"></a>需求

**標頭：** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

將檔案加入至最近使用過的 (MRU) 檔案清單。

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

*lpszPathName*<br/>
指定要加入至清單的路徑名稱。

*lpszAppID*<br/>
指定應用程式的應用程式使用者模型識別碼。

*pItem*<br/>
指定要加入至清單的 Shell 項目的指標。

*pLink*<br/>
指定殼層連結新增至清單的指標。

*pidl*<br/>
指定殼層項目應加入至新的 docs 資料夾 IDLIST。

### <a name="remarks"></a>備註

檔案名稱會新增至 MRU 清單頂端。 如果 MRU 清單中的檔案名稱已經存在，則它會移至頂端。

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

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

*n*<br/>
在功能表顯示的 MRU （最近使用的） 檔案清單編號的位移。

*lpszSection*<br/>
指向名稱登錄或應用程式的一節。其中 MRU 檔案清單會讀取和/或寫入的 INI 檔案。

*lpszEntryFormat*<br/>
指向要用於儲存在登錄或應用程式的項目名稱的格式字串。INI 檔案。

*nSize*<br/>
MRU 檔案清單中的檔案數目上限。

*nMaxDispLen*<br/>
最大長度，以字元為單位，可供常用的檔案清單中的檔名的功能表顯示。

### <a name="remarks"></a>備註

格式字串所指向*lpszEntryFormat*應該包含"%d"，這將用於取代每個 MRU 項目的索引。 例如，如果格式字串`"file%d"`則將具名項目`file0`， `file1`，依此類推。

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

取得在 MRU 檔案清單中，檔案以供使用，在功能表顯示的 MRU 清單的顯示名稱。

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
要顯示在功能表的 MRU 檔案清單中的檔案名稱的完整路徑。

*nIndex*<br/>
MRU 檔案清單中檔案的以零為起始的索引。

*lpszCurDir*<br/>
保存目前的目錄的字串。

*nCurDir*<br/>
目前的目錄字串的長度。

*bAtLeastName*<br/>
如果是非零值，指出應該傳回檔案的基底名稱項目，即使它已超過最大可顯示長度 (以傳遞*nMaxDispLen*參數來`CRecentFileList`建構函式)。

### <a name="return-value"></a>傳回值

**FALSE**如果任何檔名指定的索引中沒有最近使用過的 (MRU) 檔案清單。

### <a name="remarks"></a>備註

如果檔案是在目前的目錄，則函式會使顯示關閉的目錄。 如果檔案名稱太長，則會予以去除目錄和延伸模組。 如果仍然太長檔名，顯示名稱設為空字串除非*bAtLeastName*為非零值。

##  <a name="getsize"></a>  CRecentFileList::GetSize

擷取 MRU 檔案清單中的檔案的數目。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

在目前的檔案數目最常使用 (MRU) 檔案清單。

##  <a name="operator_at"></a>  CRecentFileList::operator]

多載註標 (`[]`) 運算子會傳回單一`CString`中以零為起始的索引所指定*nIndex*。

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
以零為起始的索引`CString`中的一組`CString`s。

##  <a name="readlist"></a>  CRecentFileList::ReadList

讀取最近使用過的 (MRU) 檔案清單，從登錄或應用程式。INI 檔案。

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

從最近使用的檔案清單移除檔案。

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要從最近使用過的 (MRU) 檔案清單中移除之檔案的以零為起始的索引。

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

更新的功能表顯示的 MRU 檔案清單。

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指標[CCmdUI](../../mfc/reference/ccmdui-class.md)最近使用過的 (MRU) 檔案清單功能表的物件。

##  <a name="writelist"></a>  CRecentFileList::WriteList

寫入至登錄或應用程式的大部分最近使用過的 (MRU) 檔案清單。INI 檔案。

```
virtual void WriteList();
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)


---
title: CFile 類別
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: a9161764f6c8646766a73add01c25cce5619ad19
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418703"
---
# <a name="cfile-class"></a>CFile 類別

MFC 檔案類別的基底類別。

## <a name="syntax"></a>語法

```
class CFile : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFile：： CFile](#cfile)|從路徑或檔案控制代碼中，建立 `CFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFile：： Abort](#abort)|關閉忽略所有警告和錯誤的檔案。|
|[CFile：： Close](#close)|關閉檔案並刪除物件。|
|[CFile：:D duplicate](#duplicate)|根據這個檔案來建立重複的物件。|
|[CFile：： Flush](#flush)|排清任何尚未寫入的資料。|
|[CFile：： GetFileName](#getfilename)|抓取選取之檔案的檔案名。|
|[CFile：： GetFilePath](#getfilepath)|抓取選取之檔案的完整檔案路徑。|
|[CFile：： GetFileTitle](#getfiletitle)|抓取選取之檔案的標題。|
|[CFile：： GetLength](#getlength)|抓取檔案的長度。|
|[CFile：： GetPosition](#getposition)|抓取目前的檔案指標。|
|[CFile：： GetStatus](#getstatus)|抓取開啟檔案的狀態，或在靜態版本中，抓取指定檔案的狀態（靜態、虛擬函數）。|
|[CFile：： LockRange](#lockrange)|鎖定檔案中的位元組範圍。|
|[CFile：： Open](#open)|安全地開啟具有錯誤測試選項的檔案。|
|[CFile：： Read](#read)|從檔案的目前檔案位置讀取（無緩衝）資料。|
|[CFile：： Remove](#remove)|刪除指定的檔案（靜態函式）。|
|[CFile：： Rename](#rename)|重新命名指定的檔案（靜態函式）。|
|[CFile：： Seek](#seek)|放置目前的檔案指標。|
|[CFile：： SeekToBegin](#seektobegin)|將目前的檔案指標置於檔案的開頭。|
|[CFile：： SeekToEnd](#seektoend)|將目前的檔案指標置於檔案結尾。|
|[CFile：： SetFilePath](#setfilepath)|設定選取之檔案的完整檔案路徑。|
|[CFile：： SetLength](#setlength)|變更檔案的長度。|
|[CFile：： SetStatus](#setstatus)|設定指定檔案的狀態（靜態、虛擬函數）。|
|[CFile：： UnlockRange](#unlockrange)|解除鎖定檔案中的位元組範圍。|
|[CFile：： Write](#write)|將檔案中的資料寫入（無緩衝）至目前的檔案位置。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFile：： operator 控制碼](#operator_handle)|`CFile` 物件的控制碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFile：： hFileNull](#hfilenull)|判斷 `CFile` 物件是否具有有效的控制碼。|
|[CFile：： m_hFile](#m_hfile)|通常包含作業系統檔案控制代碼。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CFile：： m_pTM](#m_ptm)|`CAtlTransactionManager` 物件的指標。|

## <a name="remarks"></a>備註

它會直接提供無緩衝的二進位磁片輸入/輸出服務，並透過其衍生類別間接支援文字檔和記憶體檔案。 `CFile` 與 `CArchive` 類別搭配使用，以支援序列化 Microsoft Foundation Class 物件。

這個類別及其衍生類別之間的階層式關聯性，可讓您的程式透過多型 `CFile` 介面，在所有檔案物件上運作。 例如，記憶體檔案的行為就像是磁片檔案。

針對一般用途的磁片 i/o，使用 `CFile` 和其衍生類別。 針對傳送至磁片檔案的格式化文字，使用 `ofstream` 或其他 Microsoft `iostream` 類別。

通常會在 `CFile` 結構上自動開啟磁片檔案，並在銷毀時關閉。 靜態成員函式可讓您詢問檔案的狀態，而不需要開啟檔案。

如需使用 `CFile`的詳細資訊，請參閱《*執行時間程式庫參考*》中的文章： [MFC 中](../../mfc/files-in-mfc.md)的檔和檔案[處理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="abort"></a>CFile：： Abort

關閉與此物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果您在終結物件之前尚未關閉檔案，則析構函式會為您關閉該檔案。

在處理例外狀況時，`CFile::Abort` 兩個重要的方式不同于 `CFile::Close`。 首先，`Abort` 函數不會在失敗時擲回例外狀況，因為 `Abort`會忽略失敗。 第二 **，如果檔案**尚未開啟或先前已關閉，`Abort` 將不會判斷提示。

如果您使用**new**在堆積上配置 `CFile` 物件，則必須在關閉檔案之後將其刪除。 `Abort` 會將 `m_hFile` 設定為 `CFile::hFileNull`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile：： CFile

建構並初始化 `CFile` 物件。

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>參數

*hFile*<br/>
要連結至 `CFile` 物件的檔案控制代碼。

*lpszFileName*<br/>
要連結至 `CFile` 物件的檔案相對或完整路徑。

*nOpenFlags*<br/>
指定檔案之檔案存取選項的位元組合 (OR)。 如需可能的選項，請參閱＜備註＞一節。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

下列五個數據表列出*nOpenFlags*參數的可能選項。

請僅選擇下列其中一個檔案存取模式選項。 預設檔案存取模式為 `CFile::modeRead`，其是唯讀的。

|值|描述|
|-----------|-----------------|
|`CFile::modeRead`|僅要求讀取權限。|
|`CFile::modeWrite`|僅要求寫入權限。|
|`CFile::modeReadWrite`|要求讀取和寫入權限。|

請選擇下列其中一個字元模式選項。

|值|描述|
|-----------|-----------------|
|`CFile::typeBinary`|設定二進位模式 (僅在衍生的類別中使用)。|
|`CFile::typeText`|以特殊的方式處理「換行」（僅用於衍生類別），設定文字模式。|
|`CFile::typeUnicode`|設定 Unicode 模式 (僅在衍生的類別中使用)。 當應用程式在 Unicode 組態中建置時，文字會以 Unicode 格式寫入檔案。 不會將 BOM 寫入檔案。|

請僅選擇下列其中一個檔案共用模式選項。 預設檔案共用模式為 `CFile::shareExclusive`，其是獨佔的。

|值|描述|
|-----------|-----------------|
|`CFile::shareDenyNone`|無共用限制。|
|`CFile::shareDenyRead`|拒絕所有其他項目的讀取權限。|
|`CFile::shareDenyWrite`|拒絕所有其他項目的寫入權限。|
|`CFile::shareExclusive`|拒絕所有其他項目的讀取及寫入權限。|

請選擇下列檔案的第一個，或兩者都選，以建立模式選項。 預設建立模式為 `CFile::modeNoTruncate`，其為開啟現有項目。

|值|描述|
|-----------|-----------------|
|`CFile::modeCreate`|如果檔案不存在，則建立新的檔案。 如果檔案已經存在，則會覆寫該檔案，而且一開始會設定為零長度。|
|`CFile::modeNoTruncate`|如果檔案不存在，則建立新檔案;否則，如果檔案已經存在，則會附加至 `CFile` 物件。|

請按照所述，選擇下列檔案快取選項。 根據預設，系統會使用不是選項提供的一般用途快取配置。

|值|描述|
|-----------|-----------------|
|`CFile::osNoBuffer`|系統不會使用檔案的中繼快取。 此選項會取消下列 2 個選項。|
|`CFile::osRandomAccess`|檔案快取針對隨機存取最佳化。 請勿同時使用此選項和順序掃描選項。|
|`CFile::osSequentialScan`|檔案快取針對循序存取最佳化。 請勿同時使用此選項和 [隨機存取] 選項。|
|`CFile::osWriteThrough`|寫入作業會在沒有延遲的情況下完成。|

選擇下列安全選項，以防止繼承檔案控制代碼。 根據預設，任何新子處理序都可以使用檔案控制代碼。

|值|描述|
|-----------|-----------------|
|`CFile::modeNoInherit`|防止任何子處理序使用檔案控制代碼。|

預設的函式會初始化成員，但不會將檔案附加至 `CFile` 物件。 使用此函式之後，請使用[CFile：： open](#open)方法來開啟檔案，並將它附加至 `CFile` 物件。

具有一個參數的建構函式會初始化成員，並將現有檔案連結至 `CFile` 物件。

具有兩個參數的建構函式會初始化成員，並嘗試開啟指定的檔案。 如果此建構函式成功開啟指定的檔案，則該檔案會連結至 `CFile` 物件；否則，此建構函式會擲回指向 `CInvalidArgException` 物件的指標。 如需如何處理例外狀況的詳細資訊，請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

如果 `CFile` 物件成功開啟指定的檔案，則會在終結 `CFile` 物件時自動關閉此檔案;否則，當檔案不再附加至 `CFile` 物件之後，您必須明確地關閉該檔案。

### <a name="example"></a>範例

下列程式碼顯示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile：： Close

關閉與此物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果您在終結物件之前尚未關閉檔案，則析構函式會為您關閉該檔案。

如果您使用**new**在堆積上配置 `CFile` 物件，則必須在關閉檔案之後將其刪除。 `Close` 會將 `m_hFile` 設定為 `CFile::hFileNull`。

### <a name="example"></a>範例

請參閱[CFile：： CFile](#cfile)的範例。

##  <a name="duplicate"></a>CFile：:D duplicate

為指定的檔案構造重複的 `CFile` 物件。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>傳回值

重複 `CFile` 物件的指標。

### <a name="remarks"></a>備註

此函式相當於 C 執行時間函數 `_dup`。

##  <a name="flush"></a>CFile：： Flush

強制將檔案緩衝區中剩餘的任何資料寫入檔案中。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

使用 `Flush` 並不保證會清除 `CArchive` 緩衝區。 如果您使用的是封存，請先呼叫[CArchive：： Flush](../../mfc/reference/carchive-class.md#flush) 。

### <a name="example"></a>範例

請參閱[CFile：： SetFilePath](#setfilepath)的範例。

##  <a name="getfilename"></a>CFile：： GetFileName

呼叫這個成員函式，以取出指定檔案的名稱。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>傳回值

檔案的名稱。

### <a name="remarks"></a>備註

例如，當您呼叫 `GetFileName` 為使用者產生有關檔案 `c:\windows\write\myfile.wri`的訊息時，就會傳回 filename，`myfile.wri`。

若要傳回檔案的完整路徑（包括名稱），請呼叫[GetFilePath](#getfilepath)。 若要傳回檔案的標題（`myfile`），請呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

此程式碼片段會開啟系統。WINDOWS 目錄中的 INI 檔案。 如果找到，此範例會列印出名稱和路徑和標題，如 [輸出] 底下所示：

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>CFile：： GetFilePath

呼叫這個成員函式，以取出指定檔案的完整路徑。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>傳回值

指定檔案的完整路徑。

### <a name="remarks"></a>備註

例如，當您呼叫 `GetFilePath` 為使用者產生有關檔案 `c:\windows\write\myfile.wri`的訊息時，就會傳回檔案路徑 `c:\windows\write\myfile.wri`。

若只要傳回檔案的名稱（`myfile.wri`），請呼叫[GetFileName](#getfilename)。 若要傳回檔案的標題（`myfile`），請呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

請參閱[GetFileName](#getfilename)的範例。

##  <a name="getfiletitle"></a>CFile：： GetFileTitle

呼叫這個成員函式可抓取檔案的檔案標題（顯示名稱）。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>傳回值

基礎檔案的標題。

### <a name="remarks"></a>備註

這個方法會呼叫[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)來取得檔案的標題。 如果成功，此方法會傳回系統用來向使用者顯示檔案名的字串。 否則，方法會呼叫[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)來抓取基礎檔案的檔案名（包括副檔名）。 這表示檔案副檔名不一定會包含在傳回的檔案標題字串中。 如需詳細資訊，請參閱 Windows SDK 中的[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)和[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

若要傳回檔案的完整路徑（包括名稱），請呼叫[GetFilePath](#getfilepath)。 若只要傳回檔案名，請呼叫[GetFileName](#getfilename)。

### <a name="example"></a>範例

請參閱[GetFileName](#getfilename)的範例。

##  <a name="getlength"></a>CFile：： GetLength

取得檔案目前的邏輯長度（以位元組為單位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

檔案的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>CFile：： GetPosition

取得檔案指標的目前值，可用於稍後的呼叫 `Seek`。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>傳回值

檔案指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile：： GetStatus

這個方法會抓取特定 `CFile` 物件實例或指定檔案路徑的相關狀態資訊。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*rStatus*<br/>
使用者提供之 `CFileStatus` 結構的參考，將會接收狀態資訊。 `CFileStatus` 結構具有下欄欄位：

- `CTime m_ctime` 檔案的建立日期和時間。

- `CTime m_mtime` 上次修改檔案的日期和時間。

- `CTime m_atime` 上次存取檔案以進行讀取的日期和時間。

- `ULONGLONG m_size` 檔案的邏輯大小（以位元組為單位），如 DIR 命令所報告。

- `BYTE m_attribute` 檔案的屬性位元組。

- `char m_szFullName[_MAX_PATH]` Windows 字元集中的絕對檔案名。

*lpszFileName*<br/>
Windows 字元集中的字串，這是所需檔案的路徑。 路徑可以是相對或絕對路徑，或可以包含網路路徑名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

如果成功取得指定檔案的狀態資訊，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

非靜態版本的 `GetStatus` 會抓取與指定 `CFile` 物件相關聯之開啟檔案的狀態資訊。  靜態版本的 `GetStatus` 會從指定的檔案路徑取得檔案狀態，而不需要實際開啟檔案。 這個版本適用于測試檔案的存在和存取權限。

`CFileStatus` 結構的 `m_attribute` 成員指的是檔案屬性集。 `CFile` 類別提供**屬性**列舉類型，因此可以以透過符號指定檔案屬性：

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

##  <a name="hfilenull"></a>CFile：： hFileNull

判斷 `CFile` 物件是否有有效的檔案控制代碼。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>備註

這個常數是用來判斷 `CFile` 物件是否具有有效的檔案控制代碼。

下列範例示範這項作業：

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>CFile：： LockRange

鎖定已開啟檔案中的位元組範圍，如果檔案已鎖定，則擲回例外狀況。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
要鎖定的位元組範圍開頭的位元組位移。

*dwCount*<br/>
要鎖定之範圍中的位元組數目。

### <a name="remarks"></a>備註

鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定一個以上的檔案區域，但不允許重迭的區域。

當您使用 `UnlockRange` 成員函式解除鎖定區域時，位元組範圍必須與先前鎖定的區域完全對應。 `LockRange` 函數不會合並連續的區域。 如果兩個鎖定的區域是連續的，您必須分別解除鎖定每個區域。

> [!NOTE]
>  這個函數不適用於 `CMemFile`衍生的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>CFile：： m_hFile

包含開啟檔案的作業系統檔案控制代碼。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>備註

`m_hFile` 是 UINT 類型的公用變數。 它包含 `CFile::hFileNull`，這是與作業系統無關的空白檔案指標（如果尚未指派控制碼）。

不建議使用 `m_hFile`，因為成員的意義取決於衍生的類別。 在支援非多型使用類別時，會將 `m_hFile` 設為公用成員。

##  <a name="m_ptm"></a>CFile：： m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="open"></a>CFile：： Open

已多載。 `Open` 是設計用來搭配預設的 `CFile` 的函式。

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
字串，其中包含所需檔案的路徑。 路徑可以是相對、絕對或網路名稱（UNC）。

*nOpenFlags*<br/>
定義檔案共用和存取模式的 UINT。 它會指定開啟檔案時要採取的動作。 您可以使用位 OR （ **&#124;** ）運算子來結合選項。 需要一個存取權限和一個共用選項;`modeCreate` 和 `modeNoInherit` 模式是選擇性的。 如需模式選項的清單，請參閱[CFile](#cfile)函數。

*pError*<br/>
現有檔案例外狀況物件的指標，會接收失敗作業的狀態。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

如果開啟成功，則為非零;否則為0。 只有在傳回0時， *pError*參數才有意義。

### <a name="remarks"></a>備註

這兩個 `Open` 函數是用來開啟檔案的「安全」方法，其中失敗是正常的預期條件。

雖然 `CFile` 的函式在錯誤情況下擲回例外狀況，但 `Open` 會針對錯誤狀況傳回 FALSE。 不過，`Open` 仍然可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)物件來描述錯誤。 如果您未提供*pError*參數，或如果您為*pError*傳遞 Null，`Open` 會傳回 FALSE，且不會擲回 `CFileException`。 如果您將指標傳遞至現有的 `CFileException`，而 `Open` 遇到錯誤，則函式會將描述該錯誤的資訊填入其中。 `Open` 在任一情況下都不會擲回例外狀況。

下表描述 `Open`的可能結果。

|`pError`|發生錯誤|傳回值|CFileException 內容|
|--------------|------------------------|------------------|----------------------------|
|NULL|否|TRUE|n/a|
|要 `CFileException` 的 ptr|否|TRUE|未變更|
|NULL|是|FALSE|n/a|
|要 `CFileException` 的 ptr|是|FALSE|已初始化以描述錯誤|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile：： operator 控制碼

使用此運算子，將 `CFile` 物件的控制碼傳遞至預期 `HANDLE`的函式，例如[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)和[GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) 。

```
operator HANDLE() const;
```

##  <a name="read"></a>CFile：： Read

從與 `CFile` 物件相關聯的檔案，將資料讀入緩衝區。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供之緩衝區的指標，用來接收從檔案讀取的資料。

*nCount*<br/>
要從檔案讀取的最大位元組數。 若為文字模式檔案，則會將「換行」（return line）分行符號配對計為單一字元。

### <a name="return-value"></a>傳回值

傳輸至緩衝區的位元組數目。 對於所有 `CFile` 類別而言，如果已到達檔案結尾，則傳回值可能小於*nCount* 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

如需其他範例，請參閱[CFile：： Open](#open)。

##  <a name="remove"></a>CFile：： Remove

此靜態函式會刪除路徑所指定的檔案。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
字串，這是所需檔案的路徑。 路徑可以是相對或絕對，而且可以包含網路名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

`Remove` 不會移除目錄。

如果連接的檔案已開啟或無法移除檔案，`Remove` 成員函式會擲回例外狀況。 此函式相當於 DEL 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile：： Rename

這個靜態函式會重新命名指定的檔案。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszOldName*<br/>
舊的路徑。

*lpszNewName*<br/>
新的路徑。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

無法重新命名目錄。 此函式相當於 REN 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile：： Seek

重新置放已開啟檔案中的檔案指標。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>參數

*lOff*<br/>
要移動檔案指標的位元組數目。 正值會將檔案指標移到檔案結尾，負值會將檔案指標移到檔案的開頭。

*n*<br/>
要搜尋的位置。 如需可能的值，請參閱備註一節。

### <a name="return-value"></a>傳回值

如果方法成功，則為檔案指標的位置;否則，傳回值會是未定義的，而且會擲回 `CFileException` 例外狀況的指標。

### <a name="remarks"></a>備註

下表列出*n*參數的可能值。

|值|描述|
|-----------|-----------------|
|`CFile::begin`|從檔案的開頭進行搜尋。|
|`CFile::current`|從檔案指標的目前位置進行搜尋。|
|`CFile::end`|從檔案結尾進行搜尋。|

當檔案開啟時，檔案指標會放在檔案開頭的0。

您可以將檔案指標設定為超出檔案結尾的位置。 如果您這樣做，在您寫入檔案之前，檔案大小不會增加。

此方法的例外狀況處理常式必須在處理例外狀況之後刪除例外狀況物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile：： SeekToBegin

將檔案指標的值設定為檔案的開頭。

```
void SeekToBegin();
```

### <a name="remarks"></a>備註

`SeekToBegin()` 相當於 `Seek( 0L, CFile::begin )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile：： SeekToEnd

將檔案指標的值設定為檔案的邏輯結尾。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>傳回值

檔案的長度 (以位元組為單位)。

### <a name="remarks"></a>備註

`SeekToEnd()` 相當於 `CFile::Seek( 0L, CFile::end )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>CFile：： SetFilePath

呼叫此函式可指定檔案的路徑。 例如，如果在結構化[CFile](../../mfc/reference/cfile-class.md)物件時，檔案的路徑無法使用，請呼叫 `SetFilePath` 來提供它。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>參數

*lpszNewName*<br/>
指定新路徑之字串的指標。

### <a name="remarks"></a>備註

> [!NOTE]
> `SetFilePath` 不會開啟檔案或建立檔案;它只會將 `CFile` 物件與路徑名稱產生關聯，然後再使用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>CFile：： SetLength

呼叫此函式可變更檔案的長度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>參數

*dwNewLen*<br/>
檔案所需的長度（以位元組為單位）。 這個值可能大於或小於檔案目前的長度。 檔案將會適當地擴充或截斷。

### <a name="remarks"></a>備註

> [!NOTE]
>  使用 `CMemFile`，此函數可能會擲回 `CMemoryException` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile：： SetStatus

設定與這個檔案位置相關聯之檔案的狀態。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
字串，這是所需檔案的路徑。 路徑可以是相對或絕對，而且可以包含網路名稱。

*status*<br/>
包含新狀態資訊的緩衝區。 呼叫 `GetStatus` 成員函式來 tab 具有目前值的 `CFileStatus` 結構，然後視需要進行變更。 如果值為0，則不會更新對應的狀態專案。 如需 `CFileStatus` 結構的說明，請參閱[GetStatus](#getstatus)成員函式。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

若要設定時間，請修改 [*狀態*] 的 [`m_mtime`] 欄位。

當您呼叫 `SetStatus` 以嘗試只變更檔案的屬性，而且檔案狀態結構的 `m_mtime` 成員為非零值時，屬性可能也會受到影響（變更時間戳記可能會對屬性產生副作用）。 如果您只想要變更檔案的屬性，請先將檔案狀態結構的 `m_mtime` 成員設定為零，然後再呼叫 `SetStatus`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>CFile：： UnlockRange

解除鎖定已開啟檔案中的位元組範圍。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
要解除鎖定的位元組範圍開頭的位元組位移。

*dwCount*<br/>
要解除鎖定之範圍中的位元組數目。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[LockRange](#lockrange)成員函式的描述。

> [!NOTE]
>  此函式不適用於 `CMemFile`衍生的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile：： Write

將資料從緩衝區寫入與 `CFile` 物件相關聯的檔案。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供之緩衝區的指標，其中包含要寫入檔案的資料。

*nCount*<br/>
要從緩衝區傳送的位元組數目。 若為文字模式檔案，則會將「換行」（return line）分行符號配對計為單一字元。

### <a name="remarks"></a>備註

`Write` 會擲回例外狀況，以回應數個條件，包括磁片完整的條件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

另請參閱[CFile：： CFile](#cfile)和[CFile：： Open](#open)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)

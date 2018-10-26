---
title: CFile 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a399c63903723fb35bd1b732eb15b561eeac6759
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070344"
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
|[CFile::CFile](#cfile)|建構`CFile`從路徑或檔案控制代碼的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Cfile:: Abort](#abort)|關閉檔案，並忽略所有的警告和錯誤。|
|[CFile::Close](#close)|關閉檔案，並刪除物件。|
|[CFile::Duplicate](#duplicate)|建構此檔案為基礎的重複物件。|
|[CFile::Flush](#flush)|清除任何尚未要寫入的資料。|
|[CFile::GetFileName](#getfilename)|擷取所選檔案的檔名。|
|[CFile::GetFilePath](#getfilepath)|擷取所選檔案的完整檔案路徑。|
|[CFile::GetFileTitle](#getfiletitle)|擷取所選檔案的標題。|
|[CFile::GetLength](#getlength)|擷取檔案的長度。|
|[CFile::GetPosition](#getposition)|擷取目前的檔案指標。|
|[Cfile](#getstatus)|擷取狀態開啟的檔案，或在靜態版本中，擷取指定的檔案 （靜態，虛擬函式） 的狀態。|
|[CFile::LockRange](#lockrange)|鎖定檔案中的位元組的範圍。|
|[CFile::Open](#open)|安全的錯誤測試的選項來開啟檔案。|
|[CFile::Read](#read)|讀取從目前的檔案位置的檔案 （無緩衝） 資料。|
|[CFile::Remove](#remove)|刪除指定的檔案 （靜態函式）。|
|[CFile::Rename](#rename)|重新命名指定的檔案 （靜態函式）。|
|[CFile::Seek](#seek)|將目前的檔案指標。|
|[CFile::SeekToBegin](#seektobegin)|將目前的檔案指標放置在檔案開頭。|
|[CFile::SeekToEnd](#seektoend)|將目前的檔案指標，在檔案結尾。|
|[CFile::SetFilePath](#setfilepath)|設定選取的檔案的完整檔案路徑。|
|[CFile::SetLength](#setlength)|變更檔案的長度。|
|[CFile::SetStatus](#setstatus)|設定指定的檔案 （靜態，虛擬函式） 的狀態。|
|[CFile::UnlockRange](#unlockrange)|解除鎖定檔案中的位元組的範圍。|
|[CFile::Write](#write)|（無緩衝） 將資料寫入至目前的檔案位置的檔案中。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFile::operator 控制代碼](#operator_handle)|控制代碼`CFile`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|決定如果`CFile`物件具有有效的控制代碼。|
|[CFile::m_hFile](#m_hfile)|通常會包含作業系統檔案控制代碼。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件。|

## <a name="remarks"></a>備註

它直接提供未緩衝處理、 二進位的磁碟輸入/輸出的服務，並間接支援文字檔案和記憶體檔案，透過其衍生的類別。 `CFile` 可搭配`CArchive`類別，以支援 Microsoft Foundation Class 物件的序列化。

這個類別和其衍生的類別之間的階層式關聯性可讓您透過多型的所有檔案物件上運作的程式`CFile`介面。 記憶體檔案，比方說，就等於磁碟檔案。

使用`CFile`和其衍生的類別的一般用途的磁碟 I/O。 使用`ofstream`或其他 Microsoft iostream 類別，傳送到磁碟檔案的格式化文字。

一般來說，磁碟檔案會自動開啟`CFile`建構和解構上關閉。 靜態成員函式可讓您詢問檔案的狀態，而不需要開啟檔案。

如需有關使用`CFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)並[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="abort"></a>  Cfile:: Abort

關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果您已不關閉檔案，然後再終結物件，解構函式會關閉它為您。

處理例外狀況，當`CFile::Abort`不同於`CFile::Close`兩個重要的方面。 首先，`Abort`函式不會擲回例外狀況失敗因為失敗會忽略`Abort`。 第二個，`Abort`不會**ASSERT**如果檔案尚未開啟，或先前已關閉。

如果您使用**新**配置`CFile`物件在堆積的則您必須將它刪除後關閉檔案。 `Abort` 設定`m_hFile`至`CFile::hFileNull`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>  CFile::CFile

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

下列五個表格列出可能的選項，如*nOpenFlags*參數。

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
|`CFile::typeText`|設定使用歸位字元復位換行組 （用於衍生的類別） 的特殊處理的文字模式。|
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
|`CFile::modeCreate`|如果檔案不存在，請建立新的檔案。 如果檔案已經存在，它會覆寫，且長度為零初始設定。|
|`CFile::modeNoTruncate`|如果檔案不存在，則建立新檔案；否則，如果檔案已經存在，則連結至 `CFile` 物件。|

請按照所述，選擇下列檔案快取選項。 根據預設，系統會使用尚未做為選項提供的一般目的快取配置。

|值|描述|
|-----------|-----------------|
|`CFile::osNoBuffer`|系統不會對檔案使用間歇性快取。 此選項會取消下列 2 個選項。|
|`CFile::osRandomAccess`|檔案快取針對隨機存取最佳化。 請勿使用此選項及循序掃描選項。|
|`CFile::osSequentialScan`|檔案快取針對循序存取最佳化。 請勿使用此選項及隨機存取選項。|
|`CFile::osWriteThrough`|無延遲執行寫入作業。|

選擇下列安全選項，以防止繼承檔案控制代碼。 根據預設，任何新子處理序都可以使用檔案控制代碼。

|值|描述|
|-----------|-----------------|
|`CFile::modeNoInherit`|防止任何子處理序使用檔案控制代碼。|

預設建構函式會初始化成員，但不會將檔案連結至 `CFile` 物件。 使用這個建構函式之後, 使用[CFile::Open](#open)方法來開啟檔案，並將其附加至`CFile`物件。

具有一個參數的建構函式會初始化成員，並將現有檔案連結至 `CFile` 物件。

具有兩個參數的建構函式會初始化成員，並嘗試開啟指定的檔案。 如果此建構函式成功開啟指定的檔案，則該檔案會連結至 `CFile` 物件；否則，此建構函式會擲回指向 `CInvalidArgException` 物件的指標。 如需如何處理例外狀況的詳細資訊，請參閱[例外狀況](../../mfc/exception-handling-in-mfc.md)。

如果 `CFile` 物件成功開啟指定的檔案，則它會在 `CFile` 物件終結時，自動關閉此檔案；否則，您必須在該檔案不再連結至 `CFile` 物件之後，明確關閉該檔案。

### <a name="example"></a>範例

下列程式碼顯示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果您已不關閉檔案，然後再終結物件，解構函式會關閉它為您。

如果您使用**新**配置`CFile`物件在堆積的則您必須將它刪除後關閉檔案。 `Close` 設定`m_hFile`至`CFile::hFileNull`。

### <a name="example"></a>範例

範例，請參閱[CFile::CFile](#cfile)。

##  <a name="duplicate"></a>  CFile::Duplicate

建構重複`CFile`物件指定的檔案。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>傳回值

重複的指標`CFile`物件。

### <a name="remarks"></a>備註

這相當於 C 執行階段函式`_dup`。

##  <a name="flush"></a>  CFile::Flush

強制寫入檔案的檔案緩衝區中剩餘的任何資料。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

善用`Flush`並不保證排清`CArchive`緩衝區。 如果您使用的 「 封存 」，呼叫[CArchive::Flush](../../mfc/reference/carchive-class.md#flush)第一次。

### <a name="example"></a>範例

範例，請參閱[CFile::SetFilePath](#setfilepath)。

##  <a name="getfilename"></a>  CFile::GetFileName

呼叫此成員函式，來擷取指定之檔案的名稱。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>傳回值

檔案的檔名。

### <a name="remarks"></a>備註

例如，當您呼叫`GetFileName`來產生檔案的相關使用者的訊息`c:\windows\write\myfile.wri`，檔名， `myfile.wri`，則會傳回。

若要傳回整個檔案的路徑，包括名稱、 呼叫[GetFilePath](#getfilepath)。 要傳回檔案的標題 ( `myfile`)，呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

此程式碼片段會開啟系統。在 WINDOWS 目錄中的 INI 檔案。 如果找不到，此範例會印出的名稱和路徑和標題，如輸出所示：

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

呼叫此成員函式，以擷取指定之檔案的完整路徑。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>傳回值

指定的檔案完整路徑。

### <a name="remarks"></a>備註

例如，當您呼叫`GetFilePath`來產生檔案的相關使用者的訊息`c:\windows\write\myfile.wri`，檔案路徑， `c:\windows\write\myfile.wri`，則會傳回。

要傳回檔案的名稱 (`myfile.wri`)，呼叫[GetFileName](#getfilename)。 要傳回檔案的標題 (`myfile`)，呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

範例，請參閱[GetFileName](#getfilename)。

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

呼叫此成員函式可擷取檔案的檔案標題 （顯示名稱）。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>傳回值

基礎檔案的標題。

### <a name="remarks"></a>備註

這個方法會呼叫[GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea)擷取檔案的標題。 如果成功，則方法會傳回字串，系統會用來向使用者顯示的檔案名稱。 否則，此方法會呼叫[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)來擷取基礎檔案的檔案名稱 （包括副檔名）。 因此，檔案的副檔名將不一定會包含在傳回的檔案標題字串。 如需詳細資訊，請參閱 < [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea)並[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) Windows SDK 中。

若要傳回整個檔案的路徑，包括名稱、 呼叫[GetFilePath](#getfilepath)。 若要傳回檔案的名稱，請呼叫[GetFileName](#getfilename)。

### <a name="example"></a>範例

範例，請參閱[GetFileName](#getfilename)。

##  <a name="getlength"></a>  CFile::GetLength

取得目前的邏輯長度，以位元組為單位的檔案。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

檔案的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

取得檔案指標，可在後續呼叫中的目前值`Seek`。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>傳回值

檔案指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  Cfile

這個方法會擷取相關的狀態資訊指定`CFile`物件執行個體或指定的檔案路徑。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*rStatus*<br/>
使用者提供的參考`CFileStatus`結構，將會收到狀態資訊。 `CFileStatus`結構具有下列欄位：

- `CTime m_ctime` 日期和時間的檔案所建立。

- `CTime m_mtime` 日期和上次修改檔案的時間。

- `CTime m_atime` 日期時間與上次存取檔案進行讀取。

- `ULONGLONG m_size` 邏輯大小，以位元組為單位，所報告的 DIR 命令的檔案。

- `BYTE m_attribute` 屬性檔案的位元組。

- `char m_szFullName[_MAX_PATH]` 將 Windows 字元集中的絕對檔案名稱。

*lpszFileName*<br/>
中的 Windows 字元字串也就是設定所需的檔案的路徑。 路徑可以是相對或絕對的或它可以包含網路路徑名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

如果成功取得指定的檔案的狀態資訊;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

非靜態版本`GetStatus`擷取狀態資訊相關聯的開啟檔案的指定`CFile`物件。  靜態版`GetStatus`從指定的檔案路徑取得檔案狀態，而不需要實際開啟檔案。 這是適用於測試存在與存取權限的檔案。

`m_attribute`隸屬`CFileStatus`結構參考的檔案屬性集。 `CFile`類別會提供**屬性**列舉型別，因此可以指定檔案屬性以符號形式：

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

##  <a name="hfilenull"></a>  CFile::hFileNull

判斷是否存在有效的檔案控制代碼`CFile`物件。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>備註

這個常數用來判斷如果`CFile`物件有有效的檔案控制代碼。

下列範例會示範這項作業：

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

鎖定位元組，在開啟的檔案中，擲回例外狀況，如果檔案已鎖定的範圍。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
開始的位元組範圍鎖定的位元組位移。

*dwCount*<br/>
要鎖定之範圍中的位元組數目。

### <a name="remarks"></a>備註

鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案的多個區域，但允許任何重疊的區域。

當您解除鎖定的區域時，使用`UnlockRange`成員函式，位元組範圍必須確實對應到先前鎖定的區域。 `LockRange`函式不會合併相鄰區域; 如果兩個鎖定的區域相鄰，您必須個別解除鎖定每個區域。

> [!NOTE]
>  此函式不適用於`CMemFile`-衍生的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

包含已開啟之檔案的作業系統檔案控制代碼。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>備註

`m_hFile` 是型別是 UINT 的公用變數。 它包含`CFile::hFileNull`（operating system 獨立空的檔案指標） 如果尚未指派控制代碼。

使用`m_hFile`不建議，因為該成員的意義取決於衍生類別。 `m_hFile` 會使用類別的 public 成員中支援非為了方便起見。

##  <a name="m_ptm"></a>  CFile::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

##  <a name="open"></a>  CFile::Open

多載。 `Open` 設計用於與預設`CFile`建構函式。

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
為所需的檔案路徑的字串。 路徑可以是相對、 絕對或網路名稱 (UNC)。

*nOpenFlags*<br/>
UINT 定義檔案的共用和存取模式。 它會指定要開啟的檔案時所採取的動作。 您可以使用位元 OR 結合選項 ( **&#124;** ) 運算子。 一個存取權限，以及一個共用選項是必要的資訊;`modeCreate`和`modeNoInherit`是選擇性的模式。 請參閱[CFile](#cfile)建構函式模式選項的清單。

*pError*<br/>
現有的檔案例外狀況物件，將會收到失敗作業的狀態指標。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

開啟已成功; 如果為非零否則為 0。 *PError*參數才有意義就會傳回 0。

### <a name="remarks"></a>備註

兩個函式會形成 「 安全 」 的方法，來開啟的檔案，其中失敗是正常、 預期的條件。

雖然`CFile`建構函式會擲回例外狀況發生的錯誤狀況，`Open`將錯誤條件傳回 FALSE。 `Open` 仍然可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)物件來描述錯誤，不過。 如果您未提供*pError*參數，或如果您傳遞 NULL 做*pError*，`Open`將會傳回 FALSE，並不會擲回`CFileException`。 如果您將指標傳遞至現有`CFileException`，和`Open`遇到錯誤，函式會以填滿描述該錯誤的資訊。 在不寫將`Open`擲回例外狀況。

下表說明可能的結果`Open`。

|`pError`|發生錯誤|傳回值|CFileException 內容|
|--------------|------------------------|------------------|----------------------------|
|NULL|否|true|N/A|
|若要 ptr `CFileException`|否|true|未變更|
|NULL|是|false|N/A|
|若要 ptr `CFileException`|是|false|初始化為描述錯誤|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>  CFile::operator 控制代碼

使用此運算子將控制代碼`CFile`這類物件函式[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex)並[GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) ，預期`HANDLE`。

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

資料讀取至緩衝區相關聯的檔案從`CFile`物件。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供的緩衝區會收到從檔案讀取的資料指標。

*nCount*<br/>
要從檔案讀取的位元組數目上限。 對於文字模式的檔案，換行字元復位換行組會被視為單一字元。

### <a name="return-value"></a>傳回值

傳輸至緩衝區的位元組數目。 請注意，所有`CFile`類別，傳回的值可能會小於*nCount*如果已到達檔案結尾。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

如需其他範例，請參閱[CFile::Open](#open)。

##  <a name="remove"></a>  CFile::Remove

此靜態函式會刪除指定路徑的檔案。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
為所需的檔案路徑的字串。 路徑可以是相對或絕對的而且只能包含網路名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

將不會移除目錄。

`Remove`成員函式擲回例外狀況，若未開啟連接的檔案，或無法移除檔案。 這是相當於 DEL 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

此靜態函式重新命名指定的檔案。

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

無法重新命名目錄。 這是相當於 REN 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>  CFile::Seek

在開啟的檔案中，重新放置檔案指標。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>參數

*lOff*<br/>
若要移動檔案指標的位元組數目。 正值檔案指標移到檔案結尾負值會將檔案指標朝向檔案開頭。

*nFrom*<br/>
若要從搜尋的位置。 請參閱 < 備註 > 一節，如需可能值。

### <a name="return-value"></a>傳回值

如果方法成功，檔案指標的位置否則，傳回的值是未定義和物件指標`CFileException`擲回例外狀況。

### <a name="remarks"></a>備註

下表列出可能的值，如*nFrom*參數。

|值|描述|
|-----------|-----------------|
|`CFile::begin`|從檔案開頭的搜尋。|
|`CFile::current`|從檔案指標的目前位置的搜尋。|
|`CFile::end`|從檔案結尾進行搜尋。|

當開啟檔案時，檔案指標位於 0，檔案的開頭。

您可以設定檔案指標至檔案結尾之外的位置。 如果您這麼做時，檔案的大小不會不會增加，直到您寫入檔案為止。

這個方法的例外狀況處理常式處理例外狀況之後，必須刪除例外狀況物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>  CFile::SeekToBegin

將檔案指標的值設定為 檔案的開頭。

```
void SeekToBegin();
```

### <a name="remarks"></a>備註

`SeekToBegin()` 相當於 `Seek( 0L, CFile::begin )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>  CFile::SeekToEnd

設定邏輯檔案結尾的檔案指標的值。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>傳回值

檔案的長度 (以位元組為單位)。

### <a name="remarks"></a>備註

`SeekToEnd()` 相當於 `CFile::Seek( 0L, CFile::end )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

呼叫此函式來指定檔案的路徑例如，如果檔案的路徑無法使用時[CFile](../../mfc/reference/cfile-class.md)建構物件，請呼叫`SetFilePath`提供它。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>參數

*lpszNewName*<br/>
指定新路徑的字串指標。

### <a name="remarks"></a>備註

> [!NOTE]
> `SetFilePath` 不會開啟檔案或建立檔案，只要將`CFile`路徑名稱，其可用的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

呼叫此函式來變更檔案的長度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>參數

*dwNewLen*<br/>
所需的檔案，以位元組為單位的長度。 這個值可以是檔案的大於或小於目前長度。 將會擴充或截斷為適當的檔案。

### <a name="remarks"></a>備註

> [!NOTE]
>  具有`CMemFile`，此函式可能會擲回`CMemoryException`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

設定此檔案的位置與相關聯檔案的狀態。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
為所需的檔案路徑的字串。 路徑可以是相對或絕對的而且只能包含網路名稱。

*status*<br/>
包含新的狀態資訊的緩衝區。 呼叫`GetStatus`簽名的成員函式`CFileStatus`結構和目前的值，然後依需求進行變更。 如果值為 0，則不會更新對應的狀態項目。 請參閱[GetStatus](#getstatus)成員函式的說明`CFileStatus`結構。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

若要設定的時間，修改`m_mtime`欄位*狀態*。

請注意，當您呼叫以`SetStatus`嘗試變更檔案的屬性和`m_mtime`檔案狀態結構的成員為非零值，屬性可能也會受到影響 （變更的時間戳記可能會在有副作用屬性）。 如果您想要只變更檔案的屬性，第一次設定`m_mtime`的檔案狀態結構的成員，才能為零，然後再進行呼叫`SetStatus`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

解除鎖定開啟檔案中的位元組的範圍。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*dwPos*<br/>
若要解除鎖定的位元組範圍開頭的位元組位移。

*dwCount*<br/>
要解除鎖定的範圍內的位元組數目。

### <a name="remarks"></a>備註

請參閱 popis [LockRange](#lockrange)成員函式，如需詳細資訊。

> [!NOTE]
>  此函式不適用於`CMemFile`-衍生的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>  CFile::Write

從緩衝區寫入資料至檔案與相關聯`CFile`物件。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
使用者提供的緩衝區，其中包含要寫入檔案的資料指標。

*nCount*<br/>
若要從緩衝區傳送的位元組數目。 對於文字模式的檔案，換行字元復位換行組會被視為單一字元。

### <a name="remarks"></a>備註

`Write` 以回應數個條件，包括磁碟已滿狀況，擲回的例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

此外，請參閱範例[CFile::CFile](#cfile)並[CFile::Open](#open)。

## <a name="see-also"></a>另請參閱

[MFC 範例 DRAWCLI](../../visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)

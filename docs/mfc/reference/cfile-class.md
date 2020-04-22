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
ms.openlocfilehash: 53afaf7732811e25729944eb71130a88e4f17a87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755009"
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
|[檔案檔案:檔案](#cfile)|從路徑或`CFile`檔句柄建構物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[檔案檔案::中止](#abort)|關閉忽略所有警告和錯誤的檔。|
|[檔案檔案:關閉](#close)|關閉檔案並刪除物件。|
|[檔案::D](#duplicate)|基於此檔構造重複的物件。|
|[檔檔::沖洗](#flush)|刷新尚未寫入的任何數據。|
|[檔案檔案:抓取檔案名稱](#getfilename)|檢索所選檔的檔名。|
|[檔案檔案:抓取檔案路徑](#getfilepath)|檢索選取的檔案的完整文件路徑。|
|[檔案檔案:取得檔案標題](#getfiletitle)|檢索所選檔的標題。|
|[檔案檔案:取得長度](#getlength)|檢索檔的長度。|
|[檔案檔案:抓取位置](#getposition)|檢索當前檔指標。|
|[檔案檔案:抓取狀態](#getstatus)|檢索打開檔案的狀態,或在靜態版本中檢索指定檔的狀態(靜態、虛擬函數)。|
|[檔案檔案:鎖定範圍](#lockrange)|鎖定檔中的位元組範圍。|
|[檔案檔案::開啟](#open)|使用錯誤測試選項安全地打開檔。|
|[檔案檔案:閱讀](#read)|在當前檔位置從檔讀取(未緩衝)數據。|
|[檔案檔案::刪除](#remove)|刪除指定的檔(靜態函數)。|
|[檔案檔案:重新命名](#rename)|重新命名指定的檔案(靜態函數)。|
|[檔案檔案:尋找](#seek)|定位當前檔指標。|
|[檔案檔案::尋求開始](#seektobegin)|將當前檔指標定位在檔的開頭。|
|[檔案檔::尋求結束](#seektoend)|將目前檔案指標定位到檔的末尾。|
|[檔案檔案:設定檔案路徑](#setfilepath)|設定選取的檔案的完整檔路徑。|
|[檔案檔案::設定長度](#setlength)|更改檔的長度。|
|[檔案檔案::設定狀態](#setstatus)|設置指定檔(靜態虛擬函數)的狀態。|
|[檔案檔案:解鎖範圍](#unlockrange)|解鎖檔中的位元組範圍。|
|[檔案檔案:寫入](#write)|將檔案中的數據(未緩衝)寫入當前檔案位置。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[檔案檔案::操作員手柄](#operator_handle)|`CFile`物件的句柄。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[檔案::h卷](#hfilenull)|確定`CFile`物件是否具有有效的句柄。|
|[檔::m_hFile](#m_hfile)|通常包含作業系統檔句柄。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[檔案::m_pTM](#m_ptm)|`CAtlTransactionManager` 物件的指標。|

## <a name="remarks"></a>備註

它直接提供未緩衝的二進位磁碟輸入/輸出服務,並透過派生類間接支援文本檔和記憶體檔。 `CFile`與`CArchive`類結合使用,以支援 Microsoft 基礎類物件的序列化。

此類與其派生類之間的分層關係允許程式通過多態介面`CFile`對所有文件對象進行操作。 例如,記憶體檔就像磁碟檔一樣。

通用`CFile`磁碟 I/O 的用途及其派生類。 對`ofstream`發送到磁碟檔`iostream`的 格式化文本使用或其他 Microsoft 類。

通常,磁碟檔在構造時`CFile`自動打開,並在銷毀時關閉。 靜態成員函數允許您在不打開文件的情況下詢問檔的狀態。

`CFile`有關使用的詳細資訊,請參閱[MFC](../../mfc/files-in-mfc.md)中的文章檔與*執行時庫參考*[中的檔案處理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>檔案檔案::中止

關閉與此物件關聯的檔,並使該文件無法讀取或寫入。

```
virtual void Abort();
```

### <a name="remarks"></a>備註

如果在銷毀物件之前尚未關閉該檔,析構函數將為您關閉該檔。

在處理異常時,`CFile::Abort``CFile::Close`有 兩個重要方面的不同。 首先,`Abort`函數不會在失敗時引發異常,因為`Abort`失敗被忽略。 其次,`Abort`如果檔案尚未開啟或以前已關閉, 則無法**斷言**。

如果使用**new**在`CFile`堆上 分配物件,則必須在關閉檔後將其刪除。 `Abort`集`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>檔案檔案:檔案

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

*lpszFile 名稱*<br/>
要連結至 `CFile` 物件的檔案相對或完整路徑。

*nOpenFlags*<br/>
指定檔案之檔案存取選項的位元組合 (OR)。 如需可能的選項，請參閱＜備註＞一節。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

以下五個表列出了*nOpenFlags*參數的可能選項。

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
|`CFile::typeText`|設置帶有特殊處理回車換行對的文本模式(僅在派生類中使用)。|
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
|`CFile::modeCreate`|如果沒有檔,則創建新檔。 如果檔已存在,則該檔將被覆蓋,最初設置為零長度。|
|`CFile::modeNoTruncate`|如果不存在檔,則創建新檔;否則,如果檔案已存在,則該檔案會附加到物件`CFile`。|

請按照所述，選擇下列檔案快取選項。 默認情況下,系統使用一個通用緩存方案,該方案不能作為選項提供。

|值|描述|
|-----------|-----------------|
|`CFile::osNoBuffer`|系統不為檔案使用中間緩存。 此選項會取消下列 2 個選項。|
|`CFile::osRandomAccess`|檔案快取針對隨機存取最佳化。 不要同時使用此選項和順序掃描選項。|
|`CFile::osSequentialScan`|檔案快取針對循序存取最佳化。 不要同時使用此選項和隨機訪問選項。|
|`CFile::osWriteThrough`|寫入操作無需延遲完成。|

選擇下列安全選項，以防止繼承檔案控制代碼。 根據預設，任何新子處理序都可以使用檔案控制代碼。

|值|描述|
|-----------|-----------------|
|`CFile::modeNoInherit`|防止任何子處理序使用檔案控制代碼。|

默認構造函數初始化成員,但不會將檔附加到`CFile`物件。 使用此建構函數後,使用[CFile::open](#open)方法打開檔並將其`CFile`附加到 物件。

具有一個參數的建構函式會初始化成員，並將現有檔案連結至 `CFile` 物件。

具有兩個參數的建構函式會初始化成員，並嘗試開啟指定的檔案。 如果此建構函式成功開啟指定的檔案，則該檔案會連結至 `CFile` 物件；否則，此建構函式會擲回指向 `CInvalidArgException` 物件的指標。 有關如何處理異常的詳細資訊,請參閱[異常](../../mfc/exception-handling-in-mfc.md)。

如果`CFile`物件成功打開指定的檔,它`CFile`將在銷毀物件時自動關閉此檔;如果物件成功打開指定檔,則該物件將在物件銷毀時自動關閉此檔。否則,必須在檔案不再附加到物件後顯示式關閉該檔`CFile`。

### <a name="example"></a>範例

下列程式碼顯示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>檔案檔案:關閉

關閉與此物件關聯的檔,並使該文件無法讀取或寫入。

```
virtual void Close();
```

### <a name="remarks"></a>備註

如果在銷毀物件之前尚未關閉該檔,析構函數將為您關閉該檔。

如果使用**new**在`CFile`堆上 分配物件,則必須在關閉檔後將其刪除。 `Close`集`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>範例

請參考[CFile 的範例:CFile](#cfile)。

## <a name="cfileduplicate"></a><a name="duplicate"></a>檔案::D

為給定檔構造`CFile`重複的物件。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>傳回值

指向重複`CFile`物件的指標。

### <a name="remarks"></a>備註

此函數等效於 C 執行時`_dup`函數 。

## <a name="cfileflush"></a><a name="flush"></a>檔檔::沖洗

強制將檔緩衝區中剩餘的任何數據寫入檔。

```
virtual void Flush();
```

### <a name="remarks"></a>備註

的使用`Flush`並不能保證緩衝區`CArchive`的 刷新。 如果您使用的是存檔,請先調用[CArchive::Flush。](../../mfc/reference/carchive-class.md#flush)

### <a name="example"></a>範例

請參考[CFile 的範例:設定檔案路徑](#setfilepath)。

## <a name="cfilegetfilename"></a><a name="getfilename"></a>檔案檔案:抓取檔案名稱

呼叫此成員函數以檢索指定檔的名稱。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>傳回值

檔案的名稱。

### <a name="remarks"></a>備註

例如, 當您呼`GetFileName`叫 以產生`c:\windows\write\myfile.wri`有關檔案 的訊息時,將`myfile.wri`傳回檔名 。

要傳回檔案的整個路徑 (包括名稱),請呼叫[GetFilePath](#getfilepath)。 要傳回檔案的標題 (),`myfile`請呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

此片段將打開 SYSTEM。在 WINDOWS 目錄中的 INI 檔。 如果找到,該範例將列印出名稱、路徑和標題,如「輸出」所示:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>檔案檔案:抓取檔案路徑

調用此成員函數以檢索指定檔的完整路徑。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>傳回值

指定檔的完整路徑。

### <a name="remarks"></a>備註

例如, 當您呼`GetFilePath`叫 以產生`c:\windows\write\myfile.wri`有關檔案 的訊息時,將`c:\windows\write\myfile.wri`傳回檔案路徑 。

要將傳回檔案名稱 (),`myfile.wri`請呼叫[GetFileName](#getfilename)。 要傳回檔案的標題 (),`myfile`請呼叫[GetFileTitle](#getfiletitle)。

### <a name="example"></a>範例

請參考[GetFileName 的範例](#getfilename)。

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>檔案檔案:取得檔案標題

呼叫此成員函數以檢索檔的檔案標題(顯示名稱)。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>傳回值

基礎文件的標題。

### <a name="remarks"></a>備註

此方法調用[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)來檢索文件的標題。 如果成功,該方法將返回系統用於向使用者顯示檔名的字串。 否則,該方法將調用[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)來檢索基礎檔的檔名(包括檔副檔名)。 這意味著檔案副檔名並不總是包含在返回的檔案標題字串中。 關於詳細資訊,請參閱在 Windows SDK 中[取得檔案標題](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)與[路徑尋找檔案名稱](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

要傳回檔案的整個路徑 (包括名稱),請呼叫[GetFilePath](#getfilepath)。 要將傳回檔案的名稱,請呼叫[GetFileName](#getfilename)。

### <a name="example"></a>範例

請參考[GetFileName 的範例](#getfilename)。

## <a name="cfilegetlength"></a><a name="getlength"></a>檔案檔案:取得長度

獲取檔的當前邏輯長度(以位元組為單位)。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>傳回值

檔的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>檔案檔案:抓取位置

獲取檔指標的當前值,可用於以後對`Seek`的調用。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>傳回值

檔指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>檔案檔案:抓取狀態

此方法檢索與給定`CFile`物件實例或給定文件路徑相關的狀態資訊。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*rStatus*<br/>
對將接收狀態資訊的使用者提供`CFileStatus`的結構的引用。 結構`CFileStatus`具有以下欄位:

- `CTime m_ctime`創建檔案的日期和時間。

- `CTime m_mtime`上次修改檔的日期和時間。

- `CTime m_atime`上次訪問檔的日期和時間進行讀取。

- `ULONGLONG m_size`檔的邏輯大小(以位元組為單位),由 DIR 命令報告。

- `BYTE m_attribute`檔的屬性位元組。

- `char m_szFullName[_MAX_PATH]`Windows 字元集中的絕對檔名。

*lpszFile 名稱*<br/>
Windows 字元集中的字串,它是所需檔的路徑。 路徑可以是相對路徑,也可以是絕對路徑,也可以包含網路路徑名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

如果成功獲取指定檔的狀態資訊,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

非靜態版本的`GetStatus`檢索與給`CFile`定 物件關聯的打開檔的狀態資訊。  的`GetStatus`靜態版本從給定的文件路徑獲取文件狀態,而無需實際打開檔。 此版本可用於測試檔的存在和訪問許可權。

結構`m_attribute`的成員`CFileStatus`引用檔屬性集。 類別`CFile`提供**屬性**的屬性, 以便可以象徵性的指定檔案屬性:

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

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>檔案::h卷

確定`CFile`物件的有效檔句柄是否存在。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>備註

此常量用於確定`CFile`物件是否具有有效的檔句柄。

以下範例展示此操作:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>檔案檔案:鎖定範圍

鎖定開啟檔中的位元組範圍,如果檔已鎖定,則引發異常。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*德波普斯*<br/>
要鎖定的位元組範圍開始位元組偏移。

*dw( Dw) Count*<br/>
要鎖定的範圍中的位元組數。

### <a name="remarks"></a>備註

鎖定檔案中的位元組可防止其他處理序存取這些位元組。 可以鎖定檔的多個區域,但不允許重疊區域。

使用`UnlockRange`成員函數解鎖區域時,位元組範圍必須與以前鎖定的區域完全對應。 函數`LockRange`不合併相鄰區域。 如果兩個鎖定區域相鄰,則必須單獨解鎖每個區域。

> [!NOTE]
> 此函數不適用於指定的類別`CMemFile`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>檔::m_hFile

包含打開檔的作業系統檔句柄。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>備註

`m_hFile`是 UINT 類型的公共變數。 它包含`CFile::hFileNull`,如果尚未分配句柄,則包含與操作系統無關的空檔指示器。

不建議`m_hFile`使用,因為成員的含義取決於派生類。 `m_hFile`為方便公眾支援非多態使用類。

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>檔案::m_pTM

指向 `CAtlTransactionManager` 物件的指標。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>備註

## <a name="cfileopen"></a><a name="open"></a>檔案檔案::開啟

已多載。 `Open`設計用於預設`CFile`建構函數。

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

*lpszFile 名稱*<br/>
包含所需檔案的路徑的字串。 路徑可以是相對的、絕對的還是網路名稱 (UNC)。

*nOpenFlags*<br/>
定義檔案的共享和存取模式的 UINT。 它指定打開檔時要執行的操作。 您可以使用位OR( **&#124;** ) 運算子選項. 需要一個訪問許可權和一個共用選項;`modeCreate`和`modeNoInherit`模式是可選的。 有關模式選項的清單,請參閱[CFile](#cfile)構造函數。

*pError*<br/>
指向將接收失敗操作狀態的現有文件異常物件的指標。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="return-value"></a>傳回值

如果打開成功,則非零;否則 0。 僅當返回 0 時 *,pError*參數才有意義。

### <a name="remarks"></a>備註

這兩`Open`個函數是打開檔的"安全"方法,其中故障是正常的預期條件。

當建構`CFile`函數在錯誤條件下引發異常時`Open`, 傳回 FALSE 以查找錯誤條件。 `Open`但是,仍然可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)物件來描述錯誤。 不提供*pError*參數,或是為*pError*`Open`傳遞 NULL, 則傳回`CFileException`FALSE,並且不引發 。 如果將指標傳遞給現有`CFileException`,並且`Open`遇到錯誤,則函數將填充描述該錯誤的資訊。 `Open`在這兩種情況下,都不會引發異常。

下表描述了`Open`的可能結果。

|`pError`|遇到錯誤|傳回值|檔案例外內容|
|--------------|------------------------|------------------|----------------------------|
|NULL|否|TRUE|n/a|
|ptr 到`CFileException`|否|TRUE|未變更|
|NULL|是|FALSE|n/a|
|ptr 到`CFileException`|是|FALSE|初始化以描述錯誤|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>檔案檔案::操作員手柄

`CFile`使用此運算元將句柄傳遞給物件,以將[讀取檔Ex](/windows/win32/api/fileapi/nf-fileapi-readfileex)和[GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime)等函數`HANDLE`傳遞給預期 中的函數。

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>檔案檔案:閱讀

從與物件關聯的檔案中將資料讀取到緩衝區中`CFile`。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
指向使用者提供的緩衝區的指標,該緩衝區用於接收從檔讀取的數據。

*n( N) Count*<br/>
要從文件讀取的最大位元組數。 對於文本模式檔,車廂返回行饋送對計為單個字元。

### <a name="return-value"></a>傳回值

傳輸至緩衝區的位元組數目。 對於所有`CFile`類,如果達到檔結尾,返回值可能小於*nCount。*

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

有關另一個範例,請參閱[CFile::開啟](#open)。

## <a name="cfileremove"></a><a name="remove"></a>檔案檔案::刪除

此靜態函數刪除路徑指定的檔。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
是所需檔的路徑的字串。 路徑可以是相對的,也可以是絕對的,並且可以包含網路名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

`Remove`不會刪除目錄。

如果`Remove`連接的檔處於打開狀態或無法刪除該檔,則成員函數將引發異常。 此函數等效於 DEL 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>檔案檔案:重新命名

此靜態函數重新命名指定的檔案。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszOld名稱*<br/>
老路

*lpsz 新名稱*<br/>
新路徑。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

無法重新命名目錄。 此函數等效於 REN 命令。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>檔案檔案:尋找

在打開的檔中重新置放檔案指標。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>參數

*LOff*<br/>
要移動檔指標的位元組數。 正值將檔指標移動到檔末尾;負值將檔指標移動到檔開頭。

*n 從*<br/>
位置尋求。 有關可能的值,請參閱備註部分。

### <a name="return-value"></a>傳回值

如果方法成功,則檔指標的位置;否則,返回值未定義,並引發指向異常的`CFileException`指標。

### <a name="remarks"></a>備註

下表列出了*nFrom*參數的可能值。

|值|描述|
|-----------|-----------------|
|`CFile::begin`|從文件的開頭查找。|
|`CFile::current`|從檔指標的當前位置查找。|
|`CFile::end`|從檔末尾查找。|

打開檔時,檔指標定位在 0,即檔的開頭。

您可以將檔案指標設定為檔末尾以外的位置。 如果這樣做,則檔的大小不會增加,直到您寫入該檔。

此方法的異常處理程序必須在處理異常后刪除異常物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>檔案檔案::尋求開始

將檔指標的值設置到檔的開頭。

```cpp
void SeekToBegin();
```

### <a name="remarks"></a>備註

`SeekToBegin()` 相當於 `Seek( 0L, CFile::begin )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>檔案檔::尋求結束

將檔指標的值設置到檔的邏輯端。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>傳回值

檔案的長度 (以位元組為單位)。

### <a name="remarks"></a>備註

`SeekToEnd()` 相當於 `CFile::Seek( 0L, CFile::end )`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>檔案檔案:設定檔案路徑

調用此函數以指定檔的路徑。 例如,如果在建構[CFile](../../mfc/reference/cfile-class.md)物件時檔的路徑不可用,請`SetFilePath`呼叫以提供該檔。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>參數

*lpsz 新名稱*<br/>
指向指定新路徑的字串的指標。

### <a name="remarks"></a>備註

> [!NOTE]
> `SetFilePath`不打開檔案或創建檔;它只是將`CFile`物件與路徑名稱關聯,然後可以使用路徑名稱。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>檔案檔案::設定長度

呼叫此函數以更改檔的長度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>參數

*德紐倫*<br/>
檔所需的長度(以位元組為單位)。 此值可以大於或小於檔的當前長度。 檔將根據需要擴展或截斷。

### <a name="remarks"></a>備註

> [!NOTE]
> 使用`CMemFile`時,此函數`CMemoryException`可以引發物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>檔案檔案::設定狀態

設置與此檔位置關聯的文件的狀態。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
是所需檔的路徑的字串。 路徑可以是相對的,也可以是絕對的,並且可以包含網路名稱。

*status*<br/>
包含新狀態信息的緩衝區。 調用`GetStatus`成員函數以用當前值`CFileStatus`預 填結構,然後根據需要進行更改。 如果值為 0,則相應的狀態項不會更新。 有關`CFileStatus`結構的說明,請參閱[GetStatus](#getstatus)成員函數。

*pTM*<br/>
CAtlTransactionManager 物件的指標

### <a name="remarks"></a>備註

要設定時間,請修改`m_mtime`*狀態*欄位 。

當您調用`SetStatus`以嘗試僅更改檔的屬性,並且檔狀態`m_mtime`結構 的成員是非零時,屬性也可能受到影響(更改時間戳可能對屬性產生副作用)。 如果只想更改檔案的屬性,請先將`m_mtime`檔案狀態結構的成員設定為零,然後呼`SetStatus`叫 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>檔案檔案:解鎖範圍

解鎖打開檔中的位元組範圍。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>參數

*德波普斯*<br/>
要解鎖的位元組範圍開始的位元組偏移。

*dw( Dw) Count*<br/>
要解鎖的範圍中的位元組數。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[LockRange](#lockrange)成員函數的說明。

> [!NOTE]
> 此函數不適用於指定的類別`CMemFile`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>檔案檔案:寫入

將數據從緩衝區寫入與`CFile`對象關聯的檔。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
指向使用者提供的緩衝區的指標,其中包含要寫入文件的數據。

*n( N) Count*<br/>
要從緩衝區傳輸的位元組數。 對於文本模式檔,車廂返回行饋送對計為單個字元。

### <a name="remarks"></a>備註

`Write`引發一個異常以回應多個條件,包括磁碟滿型條件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

另請參閱[CFile 的範例:CFile](#cfile)和[CFile::開啟](#open)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 類別](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)

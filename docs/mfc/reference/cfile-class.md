---
title: "CFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CFile class
- CArchive class, using with CFile
- files [C++], classes for
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: bc6edf87e5653a6aa8c749a4574c5b50fdae75a0
ms.lasthandoff: 02/24/2017

---
# <a name="cfile-class"></a>CFile 類別
MFC 檔案類別的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CFile : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFile::CFile](#cfile)|建構`CFile`從路徑或檔案的控制代碼的物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cfile:: Abort](#abort)|關閉檔案，忽略所有警告和錯誤。|  
|[CFile::Close](#close)|關閉檔案，並刪除物件。|  
|[CFile::Duplicate](#duplicate)|建構重複此檔案為基礎的物件。|  
|[CFile::Flush](#flush)|清除所有資料尚未被寫入。|  
|[CFile::GetFileName](#getfilename)|擷取所選檔案的檔名。|  
|[CFile::GetFilePath](#getfilepath)|擷取所選檔案的完整檔案路徑。|  
|[CFile::GetFileTitle](#getfiletitle)|擷取所選檔案的標題。|  
|[CFile::GetLength](#getlength)|擷取檔案的長度。|  
|[CFile::GetPosition](#getposition)|擷取目前的檔案指標。|  
|[Getstatus](#getstatus)|擷取狀態的開啟檔案，或在靜態版本中，擷取指定的檔案 （靜態、 虛擬函式） 的狀態。|  
|[CFile::LockRange](#lockrange)|鎖定檔案中的位元組的範圍。|  
|[CFile::Open](#open)|安全地開啟檔案的錯誤測試的選項。|  
|[CFile::Read](#read)|讀取目前的檔案位置的檔案資料 （未緩衝處理）。|  
|[CFile::Remove](#remove)|刪除指定的檔案 （靜態函式）。|  
|[CFile::Rename](#rename)|重新命名指定的檔案 （靜態函式）。|  
|[CFile::Seek](#seek)|將目前的檔案指標。|  
|[CFile::SeekToBegin](#seektobegin)|將目前的檔案指標放在檔案的開頭。|  
|[CFile::SeekToEnd](#seektoend)|將目前的檔案指標，該檔案的結尾。|  
|[CFile::SetFilePath](#setfilepath)|設定所選檔案的完整檔案路徑。|  
|[CFile::SetLength](#setlength)|變更檔案的長度。|  
|[CFile::SetStatus](#setstatus)|設定指定的檔案 （靜態、 虛擬函式） 的狀態。|  
|[CFile::UnlockRange](#unlockrange)|解除鎖定檔案中的位元組的範圍。|  
|[CFile::Write](#write)|將目前的檔案位置的檔案中 （緩衝） 資料。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CFile::operator 控制代碼](#operator_handle)|控制代碼`CFile`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFile::hFileNull](#hfilenull)|決定如果`CFile`物件具有有效的控制代碼。|  
|[CFile::m_hFile](#m_hfile)|通常會包含作業系統檔案控制代碼。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFile::m_pTM](#m_ptm)|指標`CAtlTransactionManager`物件。|  
  
## <a name="remarks"></a>備註  
 它直接提供未緩衝處理的二進位磁碟輸入/輸出的服務，並間接支援文字檔和透過其衍生類別的記憶體檔案。 `CFile`可搭配`CArchive`類別，以支援 Microsoft Foundation Class 物件的序列化。  
  
 這個類別及其衍生的類別之間的階層式關聯性可讓您透過多型的所有檔案物件上運作的程式`CFile`介面。 記憶體檔案，例如，行為就像磁碟檔案。  
  
 使用`CFile`和其衍生的類別的一般用途的磁碟 I/O。 使用`ofstream`或其他 Microsoft 的 iostream 類別傳送到磁碟檔案的格式化文字。  
  
 一般來說，磁碟檔案會自動開啟`CFile`建構和解構上已關閉。 靜態成員函式可讓您詢問檔案的狀態，而不需要開啟檔案。  
  
 如需有關使用`CFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="abort"></a>Cfile:: Abort  
 關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>備註  
 如果您尚未關閉檔案然後再終結物件中，解構函式會關閉它了。  
  
 當例外狀況處理、`CFile::Abort`不同於`CFile::Close`兩個重要的方式。 首先，**中止**函式不會擲回例外狀況失敗都會被忽略，因為**中止**。 第二個，**中止**不會**ASSERT**如果檔案未開啟，或先前已關閉。  
  
 如果您使用**新**配置`CFile`您必須在關閉檔案後刪除該物件在堆積上。 **Abort** sets `m_hFile` to `CFile::hFileNull`.  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&5;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]  
  
##  <a name="cfile"></a>CFile::CFile  
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
 `hFile`  
 要連結至 `CFile` 物件的檔案控制代碼。  
  
 `lpszFileName`  
 要連結至 `CFile` 物件的檔案相對或完整路徑。  
  
 `nOpenFlags`  
 指定檔案之檔案存取選項的位元組合 (OR)。 如需可能的選項，請參閱＜備註＞一節。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 下列五個表格會列出 `nOpenFlags` 參數的可能選項。  
  
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
|`CFile::typeText`|設定文字模式，對歸位字元與換行字元配對進行特殊處理 (僅在衍生類別中使用)。|  
|`CFile::typeUnicode`|設定 Unicode 模式 (僅在衍生的類別中使用)。 當應用程式在 Unicode 組態中建置時，文字會以 Unicode 格式寫入檔案。 不會將 BOM 寫入檔案。|  
  
 請僅選擇下列其中一個檔案共用模式選項。 預設檔案共用模式為 `CFile::shareExclusive`，其是獨佔的。  
  
|值|描述|  
|-----------|-----------------|  
|`CFile::shareDenyNone`|無共用限制。|  
|`CFile::shareDenyRead`|拒絕所有其他項目的讀取權限。|  
|`CFile::shareDenyWrite`|拒絕所有其他項目的寫入權限。|  
|`CFile::shareExclusive`|拒絕所有其他項目的讀取及寫入權限。|  
  
 請選擇下列檔案的第一個，或兩者都選，以建立模式選項。 預設建立模式為 `CFile::modeNoTruncate`，其為開啟現有項目。  
  
|值|說明|  
|-----------|-----------------|  
|`CFile::modeCreate`|建立新檔案，如果檔案不存在。。如果檔案已經存在， [CFileException](../../mfc/reference/cfileexception-class.md) ，就會引發。|  
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
  
 預設建構函式會初始化成員，但不會將檔案連結至 `CFile` 物件。 使用這個建構函式之後, 使用[CFile::Open](#open)方法，以開啟檔案，並將其附加至`CFile`物件。  
  
 具有一個參數的建構函式會初始化成員，並將現有檔案連結至 `CFile` 物件。  
  
 具有兩個參數的建構函式會初始化成員，並嘗試開啟指定的檔案。 如果此建構函式成功開啟指定的檔案，則該檔案會連結至 `CFile` 物件；否則，此建構函式會擲回指向 `CInvalidArgException` 物件的指標。 如需如何處理例外狀況的詳細資訊，請參閱[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
 如果 `CFile` 物件成功開啟指定的檔案，則它會在 `CFile` 物件終結時，自動關閉此檔案；否則，您必須在該檔案不再連結至 `CFile` 物件之後，明確關閉該檔案。  
  
### <a name="example"></a>範例  
 下列程式碼顯示如何使用 `CFile`。  
  
 [!code-cpp[NVC_MFCFiles #&4;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]  
  
##  <a name="close"></a>CFile::Close  
 關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 如果您尚未關閉檔案然後再終結物件中，解構函式會關閉它了。  
  
 如果您使用**新**配置`CFile`您必須在關閉檔案後刪除該物件在堆積上。 **Close** sets `m_hFile` to `CFile::hFileNull`.  
  
### <a name="example"></a>範例  
 請參閱範例[CFile::CFile](#cfile)。  
  
##  <a name="duplicate"></a>CFile::Duplicate  
 建構重複`CFile`物件指定的檔案。  
  
```  
virtual CFile* Duplicate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 重複的指標`CFile`物件。  
  
### <a name="remarks"></a>備註  
 這相當於 C 執行階段函式`_dup`。  
  
##  <a name="flush"></a>CFile::Flush  
 強制寫入檔案的檔案緩衝區中剩餘的任何資料。  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>備註  
 使用`Flush`並不保證排清`CArchive`緩衝區。 如果您使用封存，呼叫[CArchive::Flush](../../mfc/reference/carchive-class.md#flush)第一次。  
  
### <a name="example"></a>範例  
 請參閱範例[CFile::SetFilePath](#setfilepath)。  
  
##  <a name="getfilename"></a>CFile::GetFileName  
 呼叫此成員函式來擷取指定之檔案的名稱。  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的檔名。  
  
### <a name="remarks"></a>備註  
 例如，當您呼叫`GetFileName`產生檔案的相關使用者訊息`c:\windows\write\myfile.wri`，檔名， `myfile.wri`，就會傳回。  
  
 若要傳回整個檔案的路徑，包括名稱、 呼叫[GetFilePath](#getfilepath)。 要傳回的檔案名稱 ( `myfile`)，呼叫[GetFileTitle](#getfiletitle)。  
  
### <a name="example"></a>範例  
 此程式碼片段會使系統。在您的 WINDOWS 目錄中的 INI 檔案。 如果找到，則會印出名稱、 路徑及標題，輸出所示︰  
  
 [!code-cpp[NVC_MFCFiles #&6;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]  
  
##  <a name="getfilepath"></a>CFile::GetFilePath  
 呼叫此成員函式，以擷取指定之檔案的完整路徑。  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定的檔案完整路徑。  
  
### <a name="remarks"></a>備註  
 例如，當您呼叫`GetFilePath`產生檔案的相關使用者訊息`c:\windows\write\myfile.wri`，檔案路徑， `c:\windows\write\myfile.wri`，就會傳回。  
  
 若要傳回檔案的名稱 ( `myfile.wri`)，呼叫[GetFileName](#getfilename)。 要傳回的檔案名稱 ( `myfile`)，呼叫[GetFileTitle](#getfiletitle)。  
  
### <a name="example"></a>範例  
 請參閱範例[GetFileName](#getfilename)。  
  
##  <a name="getfiletitle"></a>CFile::GetFileTitle  
 呼叫此成員函式擷取檔案的標題 （顯示名稱） 的檔案。  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 基礎檔案標題。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924)擷取的檔案名稱。 如果成功，則方法會傳回系統會用來向使用者顯示的檔案名稱的字串。 否則，此方法會呼叫[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)來擷取基礎檔案的檔案名稱 （包括副檔名）。 因此，副檔名會不一定會包含在傳回的檔案標題字串。 如需詳細資訊，請參閱[GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924)和[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 若要傳回整個檔案的路徑，包括名稱、 呼叫[GetFilePath](#getfilepath)。 若要傳回檔案的名稱，請呼叫[GetFileName](#getfilename)。  
  
### <a name="example"></a>範例  
 請參閱範例[GetFileName](#getfilename)。  
  
##  <a name="getlength"></a>CFile::GetLength  
 取得目前的邏輯長度，以位元組為單位的檔案。  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的長度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&7;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]  
  
##  <a name="getposition"></a>CFile::GetPosition  
 取得目前的檔案指標，可用於後續呼叫其值`Seek`。  
  
```  
virtual ULONGLONG GetPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&8;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]  
  
##  <a name="getstatus"></a>Getstatus  
 這個方法會擷取相關的狀態資訊指定`CFile`物件執行個體或指定的檔案路徑。  
  
```  
BOOL GetStatus(CFileStatus& rStatus) const;  
  
static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,  
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>參數  
 `rStatus`  
 使用者提供的參考**CFileStatus**結構，將會收到狀態資訊。 **CFileStatus**結構具有下列欄位︰  
  
- **CTime m_ctime**建立檔案的日期和時間。  
  
- **CTime m_mtime**檔案上次修改的時間與日期。  
  
- **CTime m_atime**來讀取檔案上次存取的時間與日期。  
  
- **ULONGLONG m_size**以位元組為單位，依 DIR 命令的報告檔案的邏輯大小。  
  
- **位元組 m_attribute**檔案的屬性位元組。  
  
- **char m_szFullName [_MAX_PATH]** Windows 字元集中的絕對檔名。  
  
 `lpszFileName`  
 中的 Windows 字元字串也就是設定所需的檔案的路徑。 路徑可以是相對或絕對的或它可以包含的網路路徑名稱。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="return-value"></a>傳回值  
 **TRUE**指定檔案的狀態資訊是否已成功取得，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 非靜態版本**GetStatus**擷取狀態資訊相關聯的開啟檔案指定`CFile`物件。  靜態版**GetStatus**從指定的檔案路徑取得檔案狀態，而不需要實際開啟檔案。 這是檔案的適用於測試存在及存取權限。  
  
 **M_attribute**成員**CFileStatus**結構指的是檔案屬性集。 `CFile`類別提供**屬性**列舉型別，因此可以指定檔案屬性以透過符號︰  
  
 `enum Attribute {`  
  
 `normal =    0x00,`  
  
 `readOnly =  0x01,`  
  
 `hidden =    0x02,`  
  
 `system =    0x04,`  
  
 `volume =    0x08,`  
  
 `directory = 0x10,`  
  
 `archive =   0x20`  
  
 `};`  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&10;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]  
  
##  <a name="hfilenull"></a>CFile::hFileNull  
 判斷是否存在有效的檔案控制代碼`CFile`物件。  
  
```  
static AFX_DATA const HANDLE hFileNull;  
```  
  
### <a name="remarks"></a>備註  
 這個常數用來判斷如果`CFile`物件具有有效的檔案控制代碼。  
  
 下列範例會示範這項作業︰  
  
 [!code-cpp[NVC_MFCFiles #&22;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]  
  
##  <a name="lockrange"></a>CFile::LockRange  
 鎖定位元組中開啟的檔案，擲回例外狀況，如果檔案已鎖定的範圍。  
  
```  
virtual void LockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>參數  
 `dwPos`  
 鎖定的位元組範圍開頭的位元組位移。  
  
 `dwCount`  
 鎖定的範圍中的位元組數目。  
  
### <a name="remarks"></a>備註  
 鎖定檔案中的位元組可防止其他處理序存取這些位元組。 您可以鎖定之檔案中，多個區域，但允許沒有重疊的區域。  
  
 當您解除鎖定的區域時，使用`UnlockRange`成員函式，位元組範圍必須確實對應到先前鎖定的區域。 `LockRange`函式不會合併的相鄰區域; 如果兩個鎖定的區域是相鄰的您必須個別解除鎖定每個區域。  
  
> [!NOTE]
>  此函式不能用於`CMemFile`-衍生的類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&12;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="m_hfile"></a>CFile::m_hFile  
 包含開啟檔案的作業系統檔案控制代碼。  
  
```  
HANDLE m_hFile;  
```  
  
### <a name="remarks"></a>備註  
 `m_hFile`類型的公用變數**UINT**。 它包含`CFile::hFileNull`（操作系統獨立空白檔案指標） 如果尚未指派的控制代碼。  
  
 使用`m_hFile`不建議，因為成員的意義取決於衍生類別。 `m_hFile`是由使用類別的 public 成員以便於支援非多。  
  
##  <a name="m_ptm"></a>CFile::m_pTM  
 指向 `CAtlTransactionManager` 物件的指標。  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="open"></a>CFile::Open  
 多載。 **開啟**設計用於預設`CFile`建構函式。  
  
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
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可以是相對、 絕對或網路名稱 (UNC)。  
  
 `nOpenFlags`  
 A **UINT**所定義的檔案共用及存取模式。 它會指定要開啟檔案時所採取的動作。 您可以使用位元 OR 組合選項 ( **|** ) 運算子。 一個存取權，以及一個共用選項是必要的。**modeCreate**和**modeNoInherit**是選擇性的模式。 請參閱[CFile](#cfile)建構函式模式選項的清單。  
  
 `pError`  
 現有的檔案例外狀況物件，將會收到失敗作業的狀態指標。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="return-value"></a>傳回值  
 開啟已成功; 如果為非零否則為 0。 `pError`參數才有意義就會傳回 0。  
  
### <a name="remarks"></a>備註  
 兩個函式會形成 「 安全 」 的方法，來開啟的檔案，其中失敗是正常且預期的情況。  
  
 雖然`CFile`建構函式會擲回例外狀況時發生錯誤的情況，**開啟**會傳回**FALSE**錯誤狀況。 **開啟**仍可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)物件來描述錯誤，不過。 如果您並未提供`pError`參數，或是您傳遞**NULL**的`pError`，**開啟**會傳回**FALSE**並不會擲回`CFileException`。 如果您將指標傳遞至現有`CFileException`，和**開啟**在遇到錯誤，函式會填入它描述該錯誤的資訊。 不區分大小會在**開啟**擲回例外狀況。  
  
 下表說明可能的結果**開啟**。  
  
|`pError`|發生錯誤|傳回值|CFileException 內容|  
|--------------|------------------------|------------------|----------------------------|  
|**NULL**|否|**TRUE**|N/A|  
|ptr 至`CFileException`|否|**TRUE**|未變更|  
|**NULL**|是|**FALSE**|N/A|  
|ptr 至`CFileException`|是|**FALSE**|初始化為描述錯誤|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&13;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCFiles #&14;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]  
  
##  <a name="operator_handle"></a>CFile::operator 控制代碼  
 使用此運算子將控制代碼`CFile`這類物件傳遞給函式[ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468)和[GetFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724320) ，預期`HANDLE`。  
  
```  
operator HANDLE() const;  
```  
  
##  <a name="read"></a>CFile::Read  
 資料讀取至緩衝區相關聯的檔案從`CFile`物件。  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 從檔案讀取要接收資料的使用者提供緩衝區的指標。  
  
 `nCount`  
 要從檔案讀取的位元組數目上限。 對於文字模式的檔案，歸位換組計算為單一字元。  
  
### <a name="return-value"></a>傳回值  
 傳輸至緩衝區的位元組數目。 請注意，所有`CFile`類別，可能會傳回的值小於`nCount`如果已到達檔案結尾。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&15;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]  
  
 如需其他範例，請參閱[CFile::Open](#open)。  
  
##  <a name="remove"></a>CFile::Remove  
 這個靜態函式會刪除指定路徑的檔案。  
  
```  
static void PASCAL Remove(
    LPCTSTR lpszFileName, 
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可以是相對或絕對的且可以包含網路名稱。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 它不會移除目錄。  
  
 **移除**成員函式擲回例外狀況，如果是開啟的連接的檔案，或無法移除檔案。 這就相當於 DEL 命令。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&17;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]  
  
##  <a name="rename"></a>CFile::Rename  
 這個靜態函式會重新命名指定的檔案。  
  
```  
static void PASCAL Rename(
    LPCTSTR lpszOldName,  
    LPCTSTR lpszNewName,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszOldName`  
 舊的路徑。  
  
 `lpszNewName`  
 新的路徑。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 無法重新命名的目錄。 這就相當於 REN 命令。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&18;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]  
  
##  <a name="seek"></a>CFile::Seek  
 在開啟的檔案，重新放置檔案指標。  
  
```  
virtual ULONGLONG Seek(
LONGLONG lOff,  
UINT nFrom);
```  
  
### <a name="parameters"></a>參數  
 `lOff`  
 若要移動檔案指標的位元組數目。 正值移動檔案指標結束時的檔案。負值會將檔案指標邁向檔案的開頭。  
  
 `nFrom`  
 從搜尋的位置。 請參閱 < 備註 > 一節，取得可能的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，檔案指標的位置否則，傳回的值會是未定義的指標和`CFileException`擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 下表列出可能的值為`nFrom`參數。  
  
|值|說明|  
|-----------|-----------------|  
|`CFile::begin`|從檔案開頭進行搜尋。|  
|`CFile::current`|搜尋檔案指標的目前位置。|  
|`CFile::end`|從檔案結尾進行搜尋。|  
  
 開啟檔案時，檔案指標位於 0，檔案的開頭。  
  
 您可以設定檔案指標到超過檔案結尾。 如果您這麼做時，檔案的大小不會不會增加，直到寫入至檔案。  
  
 處理例外狀況之後，這個方法的例外狀況處理常式必須刪除例外狀況物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&9;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]  
  
##  <a name="seektobegin"></a>CFile::SeekToBegin  
 將檔案指標的值設定為檔案的開頭。  
  
```  
void SeekToBegin();
```  
  
### <a name="remarks"></a>備註  
 `SeekToBegin()` 相當於 `Seek( 0L, CFile::begin )`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&19;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="seektoend"></a>CFile::SeekToEnd  
 設定檔案指標值的邏輯檔案結尾。  
  
```  
ULONGLONG SeekToEnd();
```  
  
### <a name="return-value"></a>傳回值  
 檔案的長度 (以位元組為單位)。  
  
### <a name="remarks"></a>備註  
 `SeekToEnd()` 相當於 `CFile::Seek( 0L, CFile::end )`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&19;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="setfilepath"></a>CFile::SetFilePath  
 呼叫此函式來指定路徑的檔案。例如，如果檔案的路徑無法使用時[CFile](../../mfc/reference/cfile-class.md)建構物件，請呼叫`SetFilePath`提供。  
  
```  
virtual void SetFilePath(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>參數  
 `lpszNewName`  
 指定新路徑的字串指標。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
> `SetFilePath`不會開啟檔案或建立檔案。它只會將`CFile`路徑名稱，接著使用這些物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&20;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]  
  
##  <a name="setlength"></a>CFile::SetLength  
 呼叫此函式來變更檔案的長度。  
  
```  
virtual void SetLength(ULONGLONG dwNewLen);
```  
  
### <a name="parameters"></a>參數  
 `dwNewLen`  
 所需的檔案，以位元組為單位的長度。 這個值可以是大於或小於目前檔案的長度。 將擴充檔案，或被截斷為適當。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  使用`CMemFile`，此函式可能會擲回`CMemoryException`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&11;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]  
  
##  <a name="setstatus"></a>CFile::SetStatus  
 設定與這個檔案位置相關聯的檔案狀態。  
  
```  
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,  
    const CFileStatus& status,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可以是相對或絕對的且可以包含網路名稱。  
  
 *status*  
 緩衝區，包含新的狀態資訊。 呼叫**GetStatus**成員函式以 tab **CFileStatus**結構和目前的值，然後進行所需的變更。 如果值為 0，則不會更新對應的狀態項目。 請參閱[GetStatus](#getstatus)成員函式的說明**CFileStatus**結構。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="remarks"></a>備註  
 若要設定的時間，請修改**m_mtime**欄位*狀態*。  
  
 請注意，當您呼叫`SetStatus`，嘗試變更檔案的屬性和**m_mtime**檔案狀態結構的成員為非零值，屬性可能也會受到影響 （變更的時間戳記可能會有副作用的屬性）。 如果您想要只變更檔案屬性，先設定**m_mtime**檔案狀態結構的成員為零，然後呼叫`SetStatus`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&21;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]  
  
##  <a name="unlockrange"></a>CFile::UnlockRange  
 解除鎖定已開啟的檔案中的位元組範圍。  
  
```  
virtual void UnlockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>參數  
 `dwPos`  
 解除鎖定的位元組範圍開頭的位元組位移。  
  
 `dwCount`  
 若要解除鎖定範圍中的位元組數目。  
  
### <a name="remarks"></a>備註  
 請參閱說明[LockRange](#lockrange)成員函式，如需詳細資訊。  
  
> [!NOTE]
>  此函式不能用於`CMemFile`-衍生的類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&12;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="write"></a>CFile::Write  
 緩衝區中的資料寫入至相關聯的檔案`CFile`物件。  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 使用者提供的緩衝區，其中包含要寫入檔案的資料指標。  
  
 `nCount`  
 從緩衝區中要傳輸的位元組數目。 對於文字模式的檔案，歸位換組計算為單一字元。  
  
### <a name="remarks"></a>備註  
 **撰寫**回應數個條件，包括磁碟已滿的情況中擲回例外狀況。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&16;](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]  
  
 此外，請參閱範例[CFile::CFile](#cfile)和[CFile::Open](#open)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DRAWCLI](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [Cgopherfile 類別](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile 類別](../../mfc/reference/cmemfile-class.md)


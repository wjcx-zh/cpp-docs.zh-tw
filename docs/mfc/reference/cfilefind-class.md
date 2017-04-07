---
title: "CFileFind 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- files [C++], finding
- Internet files [C++], finding
- CFileFind class
- URLs [C++], searching for
- local files
- local files, searching for
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
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
ms.openlocfilehash: d7e6500dfc0ff24f35dd021a54080eb7ba7f1655
ms.lasthandoff: 02/24/2017

---
# <a name="cfilefind-class"></a>CFileFind 類別
執行本機檔案搜尋，而且可的基底類別[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)，，用來執行網際網路檔案搜尋。  
  
## <a name="syntax"></a>語法  
  
```  
class CFileFind : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileFind::CFileFind](#cfilefind)|建構 `CFileFind` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileFind::Close](#close)|關閉搜尋要求。|  
|[CFileFind::FindFile](#findfile)|搜尋指定的檔案名稱的目錄。|  
|[CFileFind::FindNextFile](#findnextfile)|繼續從先前呼叫該檔案[FindFile](#findfile)。|  
|[CFileFind::GetCreationTime](#getcreationtime)|取得建立檔案的時間。|  
|[CFileFind::GetFileName](#getfilename)|取得名稱，包括找到檔案的副檔名|  
|[CFileFind::GetFilePath](#getfilepath)|取得找到的檔案的完整路徑。|  
|[CFileFind::GetFileTitle](#getfiletitle)|取得找到的檔案的標題。 標題不包含副檔名。|  
|[CFileFind::GetFileURL](#getfileurl)|取得 URL，包括檔案路徑，找到的檔案。|  
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|取得檔案上次被存取的時間。|  
|[CFileFind::GetLastWriteTime](#getlastwritetime)|取得上次變更並儲存檔案的時間。|  
|[CFileFind::GetLength](#getlength)|取得找到的檔案，以位元組為單位的長度。|  
|[CFileFind::GetRoot](#getroot)|取得找到的檔案的根目錄。|  
|[CFileFind::IsArchived](#isarchived)|決定是否找到的檔案會封存。|  
|[CFileFind::IsCompressed](#iscompressed)|決定是否要壓縮找到的檔案。|  
|[CFileFind::IsDirectory](#isdirectory)|判斷是否找到的檔案目錄。|  
|[CFileFind::IsDots](#isdots)|判斷是否找到的檔案名稱具有名稱 」。 「 或 」...」，表示實際上一個目錄。|  
|[CFileFind::IsHidden](#ishidden)|決定是否找到的檔案將會隱藏。|  
|[CFileFind::IsNormal](#isnormal)|判斷是否正常找到的檔案 （亦即，沒有任何其他屬性）。|  
|[CFileFind::IsReadOnly](#isreadonly)|判斷是否找到的檔案為唯讀。|  
|[CFileFind::IsSystem](#issystem)|判斷是否找到的檔案系統檔案。|  
|[CFileFind::IsTemporary](#istemporary)|判斷是否為暫存找到的檔案。|  
|[CFileFind::MatchesMask](#matchesmask)|表示要找的檔案所需的檔案屬性。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileFind::CloseContext](#closecontext)|關閉目前的搜尋控制代碼所指定的檔案。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileFind::m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 物件的指標。|  
  
## <a name="remarks"></a>備註  
 `CFileFind`包含成員函式開始搜尋，找出檔案，並傳回標題、 名稱或檔案的路徑。 對於網際網路搜尋，成員函式[GetFileURL](#getfileurl)傳回檔案的 URL。  
  
 `CFileFind`其他兩個 MFC 類別的基底類別可用來搜尋特定的伺服器類型︰`CGopherFileFind`特別適用於 gopher 伺服器和`CFtpFileFind`特別與 FTP 伺服器的運作方式。 在一起，這三個類別提供順暢的機制，用戶端找不到檔案，不論伺服器通訊協定、 檔案類型或位置，在本機電腦或遠端伺服器上。  
  
 下列程式碼將會列舉在目前的目錄中，列印每個檔案名稱的所有檔案︰  
  
 [!code-cpp[NVC_MFCFiles #&31;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]  
  
 為了簡化範例，此程式碼會使用 c + + 標準程式庫`cout`類別。 `cout`列可取代呼叫`CListBox::AddString`，例如，在程式中使用圖形化使用者介面。  
  
 如需有關如何使用`CFileFind`和其他 WinInet 類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cfilefind"></a>CFileFind::CFileFind  
 此成員函式時，會呼叫`CFileFind`建構物件。  
  
```  
CFileFind();  
CFileFind(CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>參數  
 `pTM`  
 CAtlTransactionManager 物件的指標  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="close"></a>CFileFind::Close  
 呼叫此成員函式來結束搜尋、 重設內容，並釋放所有資源。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>備註  
 之後呼叫**關閉**，您不必建立新`CFileFind`執行個體，再呼叫[FindFile](#findfile)開始新的搜尋。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="closecontext"></a>CFileFind::CloseContext  
 關閉目前的搜尋控制代碼所指定的檔案。  
  
```  
virtual void CloseContext();
```  
  
### <a name="remarks"></a>備註  
 關閉搜尋控制代碼的目前值所指定的檔案。 覆寫這個函式來變更預設行為。  
  
 您必須呼叫[FindFile](#findfile)或[FindNextFile](#findnextfile)至少一次函式來擷取有效的搜尋控制代碼。 **FindFile**和`FindNextFile`函式會使用搜尋控制代碼來找出其名稱符合指定名稱的檔案。  
  
##  <a name="findfile"></a>CFileFind::FindFile  
 呼叫此成員函式，以開啟 檔案搜尋。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwUnused = 0);
```  
  
### <a name="parameters"></a>參數  
 `pstrName`  
 包含要尋找的檔案名稱的字串指標。 如果您傳遞**NULL**的`pstrName`， **FindFile**沒有萬用字元 (*。\*) 搜尋。  
  
 *dwUnused*  
 保留用來讓**FindFile**多型使用衍生的類別。 必須是 0。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 若要取得擴充的錯誤資訊，呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 在呼叫**FindFile**若要開始檔案搜尋，請呼叫[FindNextFile](#findnextfile)來擷取後續的檔案。 您必須呼叫`FindNextFile`至少一次之前呼叫下列屬性的任何成員函式︰  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [IsNormal](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="findnextfile"></a>CFileFind::FindNextFile  
 呼叫此成員函式，若要繼續從先前呼叫檔案搜尋[FindFile](#findfile)。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果有多個檔案。如果找到該檔案的目錄中的最後一個，或發生錯誤，則為零。 若要取得擴充的錯誤資訊，呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到該檔案的目錄中的最後一個檔案，或如果沒有相符的檔案就可以找到，`GetLastError`函式會傳回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>備註  
 您必須呼叫`FindNextFile`至少一次之前呼叫下列屬性的任何成員函式︰  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [IsNormal](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
 `FindNextFile`包裝 Win32 函式[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="getcreationtime"></a>CFileFind::GetCreationTime  
 呼叫此成員函式，以取得指定的檔案建立的時間。  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>參數  
 `pTimeStamp`  
 指標[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)結構，其中包含的檔案所建立的時間。  
  
 `refTime`  
 參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零0，如果不成功。 `GetCreationTime`只會傳回 0 [FindNextFile](#findnextfile)永遠不會呼叫這個`CFileFind`物件。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetCreationTime`。  
  
> [!NOTE]
>  並非所有的檔案系統會使用相同的語意來實作此函數所傳回的時間戳記。 此函式可能會傳回相同的值，如果基礎檔案系統或伺服器不支援保留時間屬性，其他的時間戳記函式所傳回。 請參閱[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)時間格式的相關資訊的結構。 某些作業在系統上，傳回的時間是在區域的本機電腦已為檔案所在的時間。 請參閱 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，如需詳細資訊。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getfilename"></a>CFileFind::GetFileName  
 呼叫此成員函式，以取得找到的檔案名稱。  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 最近找到檔案的名稱。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)呼叫 GetFileName 之前至少一次。  
  
 `GetFileName`是一個三個`CFileFind`傳回某種類型的檔案名稱的成員函式。 下列清單描述的三個，兩者的差異︰  
  
- `GetFileName`傳回檔案名稱，包括副檔名。 例如，呼叫`GetFileName`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案名稱`myfile.txt`。  
  
- [GetFilePath](#getfilepath)傳回整個檔案的路徑。 例如，呼叫`GetFilePath`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回的檔案路徑`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)傳回檔案名稱，不包括副檔名。 例如，呼叫`GetFileTitle`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案的標題`myfile`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&32;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]  
  
##  <a name="getfilepath"></a>CFileFind::GetFilePath  
 呼叫此成員函式，以取得指定之檔案的完整路徑。  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 將指定的檔案路徑。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetFilePath`。  
  
 `GetFilePath`是一個三個`CFileFind`傳回某種類型的檔案名稱的成員函式。 下列清單描述的三個，兩者的差異︰  
  
- [GetFileName](#getfilename)傳回檔案名稱，包括副檔名。 例如，呼叫`GetFileName`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案名稱`myfile.txt`。  
  
- `GetFilePath`傳回檔案的完整路徑。 例如，呼叫`GetFilePath`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回的檔案路徑`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)傳回檔案名稱，不包括副檔名。 例如，呼叫`GetFileTitle`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案的標題`myfile`。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getfiletitle"></a>CFileFind::GetFileTitle  
 呼叫此成員函式，以取得找到的檔案的標題。  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的標題。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetFileTitle`。  
  
 `GetFileTitle`是一個三個`CFileFind`傳回某種類型的檔案名稱的成員函式。 下列清單描述的三個，兩者的差異︰  
  
- [GetFileName](#getfilename)傳回檔案名稱，包括副檔名。 例如，呼叫`GetFileName`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案名稱`myfile.txt`。  
  
- [GetFilePath](#getfilepath)傳回整個檔案的路徑。 例如，呼叫`GetFilePath`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回的檔案路徑`c:\myhtml\myfile.txt`。  
  
- `GetFileTitle`傳回檔案名稱，不包括副檔名。 例如，呼叫`GetFileTitle`產生檔案的相關使用者訊息`c:\myhtml\myfile.txt`傳回檔案的標題`myfile`。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getfileurl"></a>CFileFind::GetFileURL  
 呼叫此成員函式擷取指定的 URL。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 完整的 URL。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetFileURL`。  
  
 `GetFileURL`成員函式類似[GetFilePath](#getfilepath)，只不過它傳回的 URL 格式`file://path`。 例如，呼叫`GetFileURL`取得的完整 URL`myfile.txt`傳回 URL `file://c:\myhtml\myfile.txt`。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime  
 呼叫此成員函式，以取得指定的檔案上次被存取的時間。  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>參數  
 `refTime`  
 參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。  
  
 `pTimeStamp`  
 指標[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)結構，其中包含檔案上次被存取的時間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零0，如果不成功。 `GetLastAccessTime`只會傳回 0 [FindNextFile](#findnextfile)永遠不會呼叫這個`CFileFind`物件。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetLastAccessTime`。  
  
> [!NOTE]
>  並非所有的檔案系統會使用相同的語意來實作此函數所傳回的時間戳記。 此函式可能會傳回相同的值，如果基礎檔案系統或伺服器不支援保留時間屬性，其他的時間戳記函式所傳回。 請參閱[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)時間格式的相關資訊的結構。 某些作業在系統上，傳回的時間是在區域的本機電腦已為檔案所在的時間。 請參閱 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，如需詳細資訊。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getlastwritetime"></a>CFileFind::GetLastWriteTime  
 呼叫此成員函式，以取得變更檔案的最後一次。  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>參數  
 `pTimeStamp`  
 指標[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)結構，其中包含檔案上次被寫入的時間。  
  
 `refTime`  
 參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零0，如果不成功。 `GetLastWriteTime`只會傳回 0 [FindNextFile](#findnextfile)永遠不會呼叫這個`CFileFind`物件。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetLastWriteTime`。  
  
> [!NOTE]
>  並非所有的檔案系統會使用相同的語意來實作此函數所傳回的時間戳記。 此函式可能會傳回相同的值，如果基礎檔案系統或伺服器不支援保留時間屬性，其他的時間戳記函式所傳回。 請參閱[Win32_Find_Data](http://msdn.microsoft.com/library/windows/desktop/aa365740)時間格式的相關資訊的結構。 某些作業在系統上，傳回的時間是在區域的本機電腦已為檔案所在的時間。 請參閱 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，如需詳細資訊。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getlength"></a>CFileFind::GetLength  
 呼叫此成員函式可取得找到的檔案，以位元組為單位的長度。  
  
```  
ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 找到檔案，以位元組為單位的長度。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetLength`。  
  
 `GetLength`使用 Win32 結構[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)取得並傳回值的檔案大小，以位元組為單位。  
  
> [!NOTE]
>  從 MFC 7.0`GetLength`支援 64 位元整數型別。 先前使用這個較新版本的程式庫建置的現有程式碼可能會導致截斷警告。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&33;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]  
  
##  <a name="getroot"></a>CFileFind::GetRoot  
 呼叫此成員函式，才能找到檔案的根目錄。  
  
```  
virtual CString GetRoot() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用中的搜尋根目錄。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`GetRoot`。  
  
 此成員函式會傳回用來開始搜尋的路徑名稱與磁碟機代碼。 例如，呼叫[FindFile](#findfile)與`*.dat`導致`GetRoot`傳回空字串。 如果傳遞路徑，例如`c:\windows\system\*.dll`至**FindFile**結果`GetRoot`傳回`c:\windows\system\`。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="isarchived"></a>CFileFind::IsArchived  
 呼叫此成員函式，來判斷是否找到的檔案會封存。  
  
```  
BOOL IsArchived() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 應用程式將封存檔案，也就是要備份或使用 FILE_ATTRIBUTE_ARCHIVE，檔案屬性中移除， [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsArchived`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="iscompressed"></a>CFileFind::IsCompressed  
 呼叫此成員函式，以判斷是否要壓縮找到的檔案。  
  
```  
BOOL IsCompressed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 壓縮的檔案會標示 FILE_ATTRIBUTE_COMPRESSED、 檔案屬性中識別[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 對於檔案，這個屬性會指出所有的檔案中的資料壓縮。 對於目錄，這個屬性會指出壓縮是新建立的檔案和子目錄的預設值。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsCompressed`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isdirectory"></a>CFileFind::IsDirectory  
 呼叫此成員函式，以判斷是否找到的檔案目錄。  
  
```  
BOOL IsDirectory() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 目錄的檔案會標示檔案屬性中所識別的 FILE_ATTRIBUTE_DIRECTORY [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsDirectory`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
 這個小程式會遞迴 C:\ 磁碟機上的每個目錄，並列印目錄的名稱。  
  
 [!code-cpp[NVC_MFCFiles #&34;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]  
  
##  <a name="isdots"></a>CFileFind::IsDots  
 呼叫此成員函式，以逐一查看檔案時測試目前的目錄與父目錄資料標記。  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果找到的檔案名稱 」。 「 或 」...」，這表示找到的檔案為實際的目錄。 否則為 0。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsDots`。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="ishidden"></a>CFileFind::IsHidden  
 呼叫以判斷找到的檔案是否隱藏此成員函式。  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 中所識別的隱藏的檔，以 FILE_ATTRIBUTE_HIDDEN 標示，檔案屬性[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 隱藏的檔案未包含在一般的目錄清單中。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsHidden`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isnormal"></a>CFileFind::IsNormal  
 呼叫此成員函式，以判斷找到的檔案是否為一般的檔案。  
  
```  
BOOL IsNormal() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 標有 FILE_ATTRIBUTE_NORMAL 檔案，檔案屬性中所識別[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 一般檔案沒有任何其他設定的屬性。 所有其他檔案屬性覆寫這個屬性。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsNormal`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isreadonly"></a>CFileFind::IsReadOnly  
 呼叫此成員函式，以判斷找到的檔案是否唯讀。  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 唯讀的檔案會標示 FILE_ATTRIBUTE_READONLY、 檔案屬性中識別[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 應用程式可以讀取檔案，但是無法寫入或刪除它。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsReadOnly`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="issystem"></a>CFileFind::IsSystem  
 呼叫此成員函式，以判斷是否找到的檔案系統檔案。  
  
```  
BOOL IsSystem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 FILE_ATTRIBUTE_SYSTEM，都會標示系統檔案、 檔案屬性中識別[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 系統檔案是一部分使用，或所獨佔使用，作業系統。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsSystem`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="istemporary"></a>CFileFind::IsTemporary  
 呼叫此成員函式，以判斷找到的檔案是否暫存檔。  
  
```  
BOOL IsTemporary() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 暫存檔案會標示 FILE_ATTRIBUTE_TEMPORARY、 檔案屬性中識別[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構。 暫存檔案會用於暫存儲存體。 只有在絕對必要時，應用程式應該寫入檔案。 大部分的檔案的資料會保存在記憶體中，而不會排清到媒體中，因為很快就會刪除檔案。  
  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`IsTemporary`。  
  
 請參閱成員函式[MatchesMask](#matchesmask)檔案屬性的完整清單。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileFind::GetLength](#getlength)。  
  
##  <a name="m_ptm"></a>CFileFind::m_pTM  
 指向 `CAtlTransactionManager` 物件的指標。  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="matchesmask"></a>CFileFind::MatchesMask  
 呼叫此成員函式，以測試檔案屬性上找到的檔案。  
  
```  
virtual BOOL MatchesMask(DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwMask`  
 指定一或多個檔案屬性，識別在[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)結構中的，找到檔案。 若要搜尋多個屬性，使用位元 OR (|) 運算子。 是可接受的下列屬性的任何組合︰  
  
-   FILE_ATTRIBUTE_ARCHIVE 檔案是保存檔案。 應用程式會使用這個屬性，將檔案備份或移除標記。  
  
-   壓縮 FILE_ATTRIBUTE_COMPRESSED 檔案或目錄。 對於檔案，這表示所有檔案中的資料壓縮。 對於目錄而言，這表示壓縮是新建立的檔案和子目錄的預設值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 檔案是目錄。  
  
-   FILE_ATTRIBUTE_NORMAL 檔案具有未設定其他屬性。 這個屬性是單獨使用時才有效。 所有其他檔案屬性覆寫這個屬性。  
  
-   FILE_ATTRIBUTE_HIDDEN 隱藏的檔案。 它並不包含在一般的目錄清單。  
  
-   FILE_ATTRIBUTE_READONLY 檔案是唯讀的。 應用程式可以讀取檔案，但無法寫入或刪除它。  
  
-   FILE_ATTRIBUTE_SYSTEM 檔案的一部分或作業系統所獨佔使用。  
  
-   FILE_ATTRIBUTE_TEMPORARY 檔案用於暫存儲存體。 只有在絕對必要時，應用程式應該寫入檔案。 大部分的檔案的資料會保存在記憶體中，而不會排清到媒體中，因為很快就會刪除檔案。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 若要取得擴充的錯誤資訊，呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[FindNextFile](#findnextfile)至少一次，才能呼叫`MatchesMask`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&35;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind 類別](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 類別](../../mfc/reference/chttpfile-class.md)


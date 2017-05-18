---
title: "CInternetFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
dev_langs:
- C++
helpviewer_keywords:
- CInternetFile class
- Internet files
- Internet files, CInternetFile class
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e1d6227ebd642025e6b00019518d29080cf0454
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cinternetfile-class"></a>CInternetFile 類別
允許使用網際網路通訊協定的遠端系統上之檔案的存取。  
  
## <a name="syntax"></a>語法  
  
```  
class CInternetFile : public CStdioFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](#cinternetfile)|建構 `CInternetFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|關閉檔案，並忽略所有警告和錯誤。|  
|[CInternetFile::Close](#close)|關閉`CInternetFile`，並釋放其資源。|  
|[CInternetFile::Flush](#flush)|排清寫入緩衝區的內容，並確定記憶體中的資料會寫入到目標電腦。|  
|[CInternetFile::GetLength](#getlength)|傳回檔案的大小。|  
|[CInternetFile::Read](#read)|讀取指定的位元組數。|  
|[CInternetFile::ReadString](#readstring)|讀取資料流的字元。|  
|[CInternetFile::Seek](#seek)|指標重新置放在開啟的檔案。|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|設定緩衝區的大小會讀取資料。|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|設定要在其中寫入資料的緩衝區大小。|  
|[CInternetFile::Write](#write)|寫入指定的位元組數目。|  
|[CInternetFile::WriteString](#writestring)|以 null 結束的字串寫入檔案。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|網際網路控制代碼的轉型運算子。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|檔案控制代碼。|  
  
## <a name="remarks"></a>備註  
 提供基底類別[CHttpFile](../../mfc/reference/chttpfile-class.md)和[CGopherFile](../../mfc/reference/cgopherfile-class.md)檔案類別。 絕對不要建立`CInternetFile`直接物件。 相反地，來建立物件的其中一個衍生類別呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您也可以建立`CInternetFile`物件呼叫[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。  
  
 `CInternetFile`成員函式**開啟**， `LockRange`， `UnlockRange`，和`Duplicate`並未實作`CInternetFile`。 如果您呼叫這些函式上`CInternetFile`物件時，就會[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要深入了解如何`CInternetFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [Cgopherfile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
  
##  <a name="abort"></a>CInternetFile::Abort  
 關閉與這個物件相關聯的檔案，並使檔案無法讀取或寫入。  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>備註  
 如果您尚未關閉檔案然後再終結物件中，解構函式會關閉它了。  
  
 當例外狀況處理、**中止**不同於[關閉](#close)兩個重要的方式。 首先，**中止**函式不會擲回例外狀況失敗因為它會忽略失敗。 第二個，**中止**不**ASSERT**如果檔案未開啟，或先前已關閉。  
  
##  <a name="cinternetfile"></a>CInternetFile::CInternetFile  
 此成員函式時，會呼叫`CInternetFile`建立物件。  
  
```  
CInternetFile(
    HINTERNET hFile,  
    LPCTSTR pstrFileName,  
    CInternetConnection* pConnection,  
    BOOL bReadMode);

 
CInternetFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrFileName,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext,  
    BOOL bReadMode);
```  
  
### <a name="parameters"></a>參數  
 `hFile`  
 網際網路檔案控制代碼。  
  
 `pstrFileName`  
 包含檔案名稱的字串指標。  
  
 `pConnection`  
 指標[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件。  
  
 *bReadMode*  
 指出檔案是否為唯讀。  
  
 `hSession`  
 網際網路工作階段控制代碼。  
  
 `pstrServer`  
 包含伺服器名稱的字串指標。  
  
 `dwContext`  
 內容識別碼`CInternetFile`物件。 請參閱[WinInet 基本概念](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
### <a name="remarks"></a>備註  
 絕對不要建立`CInternetFile`直接物件。 相反地，來建立物件的其中一個衍生類別呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)。 您也可以建立`CInternetFile`物件呼叫[CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)。  
  
##  <a name="close"></a>CInternetFile::Close  
 關閉`CInternetFile`並釋放任何它的資源。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 如果已開啟檔案以供寫入，則隱含呼叫[排清](#flush)以確保所有緩衝資料寫入至主機。 您應該呼叫**關閉**當您完成使用檔案。  
  
##  <a name="flush"></a>CInternetFile::Flush  
 呼叫此成員函式，以排清寫入緩衝區的內容。  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>備註  
 使用`Flush`以確保記憶體中的所有資料到目標電腦實際上已都寫入，以確保您具有主機上的交易已完成。 `Flush`才有效上`CInternetFile`物件開啟以供寫入。  
  
##  <a name="getlength"></a>CInternetFile::GetLength  
 傳回檔案的大小。  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>CInternetFile::m_hFile  
 與這個物件相關聯的檔案控制代碼。  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>CInternetFile::operator HINTERNET  
 您可以使用這個運算子來取得目前的網際網路工作階段的視窗控制代碼。  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>CInternetFile::Read  
 呼叫此成員函式以讀取到指定的記憶體，從 `lpvBuf` 開始，指定的位元組數目為 `nCount`。  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 將檔案資料讀取到的記憶體位址指標。  
  
 `nCount`  
 要寫入的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳輸至緩衝區的位元組數目。 如果已達到檔案結尾，傳回的值可能小於 `nCount`。  
  
### <a name="remarks"></a>備註  
 此函數會傳回實際讀取的位元組數目 — 可能小於 `nCount` 的數字 (如果檔案結束)。 如果在讀取檔案時發生錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。 請注意，讀取超過檔案結尾不被視為錯誤，而且會擲回任何例外狀況。  
  
 若要確保擷取所有資料，應用程式必須繼續呼叫**CInternetFile::Read**方法，直到此方法會傳回零。  
  
##  <a name="readstring"></a>CInternetFile::ReadString  
 呼叫此成員函式可讀取的字元資料流，直到找到新行字元。  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 將會收到所讀取的行的字串指標。  
  
 `nMax`  
 要讀取的字元數目上限。  
  
 `rString`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收讀取的行的物件。  
  
### <a name="return-value"></a>傳回值  
 包含一般從擷取的資料緩衝區的指標[CInternetFile](../../mfc/reference/cinternetfile-class.md)物件。 傳遞至這個方法的緩衝區的資料型別，不論它不會執行任何操作資料 （例如，轉換成 Unicode），因此您必須將傳回的資料對應至結構，您預期，如同**void\* **傳回型別。  
  
 **NULL**檔案結尾已到達未讀取任何資料; 如果或布林值，如果**FALSE**如果檔案結尾已到達未讀取任何資料。  
  
### <a name="remarks"></a>備註  
 函式會產生列放入所參考的記憶體`pstr`參數。 它會停止讀取字元達到指定的字元數目上限時`nMax`。 緩衝區一定會收到結束的 null 字元。  
  
 如果您呼叫`ReadString`但是未先呼叫[SetReadBufferSize](#setreadbuffersize)，就會為 4096 位元組的緩衝區。  
  
##  <a name="seek"></a>CInternetFile::Seek  
 呼叫此成員函式，以重新整理指標先前開啟的檔案。  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>參數  
 `lOffset`  
 以位元組為單位來移動檔案中的讀取/寫入指標的位移。  
  
 `nFrom`  
 相對位移的參考。 必須是下列值之一︰  
  
- **CFile::begin**移動檔案指標`lOff`轉寄從檔案開頭的位元組。  
  
- **CFile::current**移動檔案指標`lOff`位元組從目前位置的檔案中。  
  
- **CFile::end**移動檔案指標`lOff`從檔案結尾的位元組。 `lOff`必須為負數來搜尋現有的檔案。正值會搜尋超出檔案結尾。  
  
### <a name="return-value"></a>傳回值  
 新要求的位置是合法的如果從檔案開頭位移的位元組否則，這個值是未定義和[CInternetException](../../mfc/reference/cinternetexception-class.md)物件就會擲回。  
  
### <a name="remarks"></a>備註  
 `Seek`函式允許隨機存取檔案的內容移動指標指定的數量，具有絕對或相對。 在搜尋期間實際不讀取任何資料。  
  
 此時，此成員函式的呼叫僅支援與相關聯資料`CHttpFile`物件。 不支援 FTP 和 gopher 的要求。 如果您呼叫`Seek`的其中一個不支援服務，它會傳回您 Win32 錯誤碼**ERROR_INTERNET_INVALID_OPERATION**。  
  
 開啟檔案時，檔案指標是在位移 0，檔案的開頭。  
  
> [!NOTE]
>  使用`Seek`可能會造成的隱含呼叫[排清](#flush)。  
  
### <a name="example"></a>範例  
  請參閱基底類別實作的範例 ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek))。  
  
##  <a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize  
 呼叫此成員函式所使用的暫時讀取緩衝區的大小設定`CInternetFile`-衍生物件。  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>參數  
 *nReadSize*  
 需要的緩衝區大小 (以位元組為單位)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 基礎 WinInet Api 不要執行緩衝處理，所以請選擇可讓您的應用程式，無論要讀取的資料量，有效地讀取資料的緩衝區大小。 如果每個呼叫[讀取](#read)通常牽涉到大型 aount 的資料 （例如，四個或多個 kb 為單位），您應該不需要的緩衝區。 不過，如果您呼叫**讀取**取得小塊資料，或如果您使用[ReadString](#readstring)一次讀取個別的線條，然後讀取的緩衝區改進應用程式效能。  
  
 根據預設，`CInternetFile`物件不提供讀取的緩衝處理。 如果您呼叫此成員函式時，您必須確定已開啟檔案進行讀取存取權。  
  
 您可以在任何時間，增加緩衝區大小，但壓縮緩衝區會有任何作用。 如果您呼叫[ReadString](#readstring)但是未先呼叫`SetReadBufferSize`，就會為 4096 位元組的緩衝區。  
  
##  <a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize  
 呼叫此成員函式所使用的暫時寫入緩衝區的大小設定`CInternetFile`-衍生物件。  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>參數  
 *nWriteSize*  
 以位元組為單位的緩衝區大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 基礎 WinInet Api 不執行緩衝處理，因此選擇可讓您的應用程式有效率地不論要寫入的資料量的資料寫入緩衝區大小。 如果每個呼叫[撰寫](#write)通常牽涉到大量的資料 (例如，四個 kb 或更多一次），您應該不需要的緩衝區。 不過，如果您呼叫[撰寫](#write)寫入緩衝區寫入小塊資料，改善應用程式的效能。  
  
 根據預設，`CInternetFile`物件不提供任何緩衝進行寫入。 如果您呼叫此成員函式時，您必須確定已開啟檔案進行寫入存取權。 您可以在任何時間，變更寫入緩衝區的大小，但這樣做，就會導致的隱含呼叫[排清](#flush)。  
  
##  <a name="write"></a>CInternetFile::Write  
 呼叫此成員函式寫入至指定的記憶體， `lpvBuf`、 指定的位元組數目， `nCount`。  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>參數  
 `lpBuf`  
 要寫入的第一個位元組指標。  
  
 `nCount`  
 指定要寫入的位元組數目。  
  
### <a name="remarks"></a>備註  
 如果在寫入資料時發生任何錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。  
  
##  <a name="writestring"></a>CInternetFile::WriteString  
 此函式會以 null 結束的字串寫入相關聯的檔案。  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>參數  
 `pstr`  
 字串，包含要寫入的內容指標。  
  
### <a name="remarks"></a>備註  
 如果在寫入資料時發生任何錯誤，函式會擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)描述錯誤的物件。  
  
## <a name="see-also"></a>另請參閱  
 [Cgopherfile 類別](../../mfc/reference/cstdiofile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)


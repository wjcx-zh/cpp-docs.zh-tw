---
title: "Cinternetfile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
dev_langs: C++
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e9af23bb74ba8e96f29a5b7cc4139d2932df8c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="chttpfile-class"></a>Cinternetfile 類別
提供在 HTTP 伺服器上要求和讀取檔案的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHttpFile::CHttpFile](#chttpfile)|建立 `CHttpFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|將傳送至 HTTP 伺服器的要求標頭。|  
|[CHttpFile::EndRequest](#endrequest)|結束傳送至與 HTTP 伺服器要求[SendRequestEx](#sendrequestex)成員函式。|  
|[CHttpFile::GetFileURL](#getfileurl)|取得指定的檔案的 URL。|  
|[CHttpFile::GetObject](#getobject)|HTTP 伺服器要求中取得動詞命令的目標物件。|  
|[CHttpFile::GetVerb](#getverb)|取得與 HTTP 伺服器要求所使用的動詞命令。|  
|[CHttpFile::QueryInfo](#queryinfo)|從 HTTP 伺服器傳回的回應或要求標頭。|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|擷取 HTTP 要求相關聯的狀態碼，並將它放在提供`dwStatusCode`參數。|  
|[CHttpFile::SendRequest](#sendrequest)|將要求傳送至 HTTP 伺服器。|  
|[CHttpFile::SendRequestEx](#sendrequestex)|將要求傳送至 HTTP 伺服器使用[寫入](../../mfc/reference/cinternetfile-class.md#write)或[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。|  
  
## <a name="remarks"></a>備註  
 如果您的網際網路工作階段會從 HTTP 伺服器讀取資料，您必須建立的執行個體`CHttpFile`。  
  
 若要深入了解如何`CHttpFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [Cgopherfile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders  
 呼叫此成員函式中加入一個或多個 HTTP 要求的 HTTP 要求標頭處理。  
  
```  
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,  
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,  
    int dwHeadersLen = -1);

 
BOOL AddRequestHeaders(
    CString& str,  
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```  
  
### <a name="parameters"></a>參數  
 `pstrHeaders`  
 包含標頭或要附加至要求的標頭的字串指標。 必須以 CR/LF 組來結束每個標頭。  
  
 `dwFlags`  
 修改新的標頭的語意。 可以是下列其中一項：  
  
- `HTTP_ADDREQ_FLAG_COALESCE`合併相同的名稱，請使用旗標新增到後續的標頭中找到的第一個標頭的標頭。 比方說，「 接受： 文字 / *"後面接著"接受： 音訊 /\*"形成一個標頭會導致"接受： 文字 /\*音訊 /\*"。 這是由呼叫的應用程式，以確保凝聚力配置相對於與聯合或個別標頭傳送的要求所接收的資料。  
  
- `HTTP_ADDREQ_FLAG_REPLACE`執行移除並新增至取代目前標頭。 標頭名稱會用來移除目前的標頭，以及完整的值會用來加入新的標頭。 如果標頭值是空白，而且標頭，則會將它移除。 如果不是空的標頭值取代。  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW`如果不存在，只會加入標頭。 如果有的話，則會傳回錯誤。  
  
- `HTTP_ADDREQ_FLAG_ADD`使用 with REPLACE。 如果不存在，請加入標頭。  
  
 `dwHeadersLen`  
 長度，以字元為單位的`pstrHeaders`。 如果這是-1l; 此時則`pstrHeaders`假設為零結束，而且長度會計算。  
  
 `str`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要加入標頭的要求標頭。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 `AddRequestHeaders`將其他的自由格式的標頭附加至 HTTP 要求控制代碼。 它適用於複雜的用戶端，都需要詳細的確實要求傳送至 HTTP 伺服器控制。  
  
> [!NOTE]
>  應用程式可以將多個標頭中的傳遞`pstrHeaders`或`str`如`AddRequestHeaders`使用呼叫`HTTP_ADDREQ_FLAG_ADD`或`HTTP_ADDREQ_FLAG_ADD_IF_NEW`。 如果應用程式會嘗試移除或取代標頭使用**HTTP_ADDREQ_FLAG_REMOVE**或`HTTP_ADDREQ_FLAG_REPLACE`，只有一個標頭可以提供在`lpszHeaders`。  
  
##  <a name="chttpfile"></a>CHttpFile::CHttpFile  
 呼叫此成員函式會建構`CHttpFile`物件。  
  
```  
CHttpFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrObject,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrVerb,  
    DWORD_PTR dwContext);

 
CHttpFile(
    HINTERNET hFile,  
    LPCTSTR pstrVerb,  
    LPCTSTR pstrObject,  
    CHttpConnection* pConnection);
```  
  
### <a name="parameters"></a>參數  
 `hFile`  
 網際網路檔案控制代碼。  
  
 `hSession`  
 網際網路工作階段控制代碼。  
  
 *pstrObject*  
 字串，包含指標`CHttpFile`物件。  
  
 `pstrServer`  
 包含伺服器名稱的字串指標。  
  
 `pstrVerb`  
 指向的字串，包含要傳送要求時使用的方法。 可以是**POST**， **HEAD**，或`GET`。  
  
 dwContext  
 內容識別項`CHttpFile`物件。 請參閱**備註**如需有關此參數。  
  
 `pConnection`  
 指標[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件。  
  
### <a name="remarks"></a>備註  
 您永遠不會建構`CHttpFile`直接物件; 而是呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)改為。  
  
 預設值為`dwContext`MFC 所傳送的`CHttpFile`物件從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫`CInternetSession::OpenURL`或`CHttpConnection`建構`CHttpFile`物件，您可以覆寫預設值，您選擇的值來設定內容識別碼。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供其所識別的物件上的狀態。 請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="endrequest"></a>CHttpFile::EndRequest  
 呼叫此成員函式，來結束傳送至與 HTTP 伺服器要求[SendRequestEx](#sendrequestex)成員函式。  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 描述作業的旗標。 如需適當的旗標的清單，請參閱[HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) Windows SDK 中。  
  
 `lpBuffIn`  
 指標初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用於作業的輸入的緩衝區。  
  
 `dwContext`  
 內容識別項`CHttpFile`作業。 此參數的相關資訊，請參閱 < 備註 >。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 預設值為`dwContext`MFC 所傳送的`CHttpFile`物件從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)建構`CHttpFile`物件，您可以覆寫預設值，您選擇的值來設定內容識別碼。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供其所識別的物件上的狀態。 請參閱文件[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="getfileurl"></a>CHttpFile::GetFileURL  
 呼叫此成員函式可取得做為 URL 的 HTTP 檔案的名稱。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含參考與此檔案相關聯的資源的 URL。  
  
### <a name="remarks"></a>備註  
 使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="getobject"></a>CHttpFile::GetObject  
 呼叫此成員函式，取得與此相關聯的物件名稱`CHttpFile`。  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含物件的名稱。  
  
### <a name="remarks"></a>備註  
 使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="getverb"></a>CHttpFile::GetVerb  
 呼叫此成員函式，取得 HTTP 動詞命令 （或方法） 與此相關聯`CHttpFile`。  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含 HTTP 動詞命令 （或方法） 的名稱。  
  
### <a name="remarks"></a>備註  
 使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
##  <a name="queryinfo"></a>CHttpFile::QueryInfo  
 呼叫此成員函式，以傳回回應，或要求標頭從 HTTP 要求。  
  
```  
BOOL QueryInfo(
    DWORD dwInfoLevel,  
    LPVOID lpvBuffer,  
    LPDWORD lpdwBufferLength,  
    LPDWORD lpdwIndex = NULL) const;  
  
BOOL QueryInfo(
    DWORD dwInfoLevel,  
    CString& str,  
    LPDWORD dwIndex = NULL) const;  
  
BOOL QueryInfo(
    DWORD dwInfoLevel,  
    SYSTEMTIME* pSysTime,  
    LPDWORD dwIndex = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwInfoLevel`  
 要查詢和下列旗標會指定要求的資訊類型的屬性組合：  
  
- **HTTP_QUERY_CUSTOM**尋找標頭名稱並傳回此值在`lpvBuffer`輸出上。 **HTTP_QUERY_CUSTOM**擲回的判斷提示，如果找不到標頭。  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS**一般而言，應用程式會查詢回應標頭，但應用程式也可以查詢要求標頭使用這個旗標。  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME**這些標頭，其值為日期/時間字串，例如 「 上次修改時間，"這個旗標會傳回標準 Win32 的標頭值[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)不需要的結構剖析資料的應用程式。 如果您使用這個旗標時，您可能想要使用`SYSTEMTIME`函式的覆寫。  
  
- **HTTP_QUERY_FLAG_NUMBER**這些標頭，其值是數字，例如狀態程式碼中，這個旗標傳回資料當做 32 位元數字。  
  
 請參閱**備註**部分的可能值清單。  
  
 `lpvBuffer`  
 接收資訊之緩衝區的指標。  
  
 `lpdwBufferLength`  
 項目，這會指向包含資料緩衝區的字元數或位元組長度的值。 請參閱**備註**如需詳細資訊，此參數的相關區段。  
  
 `lpdwIndex`  
 標頭以零為起始索引指標。 可以是**NULL**。 使用這個旗標列舉多個具有相同名稱的標頭。 輸入時，`lpdwIndex`表示傳回指定的標頭的索引。 在輸出時，`lpdwIndex`指出下一步的標頭的索引。 如果找不到下一個索引， **ERROR_HTTP_HEADER_NOT_FOUND**傳回。  
  
 `str`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收傳回的資訊的物件。  
  
 `dwIndex`  
 索引值。 請參閱 `lpdwIndex`。  
  
 *pSysTime*  
 對 win32 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 您可以擷取下列類型的資料從`QueryInfo`:  
  
-   字串 （預設值）  
  
- `SYSTEMTIME`(如 「 資料:""的到期日:"等，標頭)  
  
- `DWORD`(如**STATUS_CODE**， **CONTENT_LENGTH**等。)  
  
 當字串會寫入至緩衝區，而成員函式成功，`lpdwBufferLength`包含減 1 結束的字元字串的長度**NULL**字元。  
  
 可能的`dwInfoLevel`值包括：  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode  
 呼叫此成員函式，取得 HTTP 要求相關聯的狀態碼，並將它放在提供`dwStatusCode`參數。  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwStatusCode`  
 狀態程式碼的參考。 狀態代碼表示成功或失敗的要求的事件。 請參閱**備註**狀態程式碼說明選項。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
### <a name="remarks"></a>備註  
 使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
 HTTP 狀態碼可分為群組指出成功或失敗的要求。 下表概述狀態程式碼群組及最常見的 HTTP 狀態碼。  
  
|群組|意義|  
|-----------|-------------|  
|200-299|成功|  
|300-399|資訊|  
|400-499|要求錯誤|  
|500-599|伺服器錯誤|  
  
 常見的 HTTP 狀態碼：  
  
|狀態碼|意義|  
|-----------------|-------------|  
|200|找到 URL，接著進行傳輸|  
|400|難以理解的要求|  
|404|找不到要求的 URL|  
|405|伺服器不支援所要求的方法|  
|500|未知的伺服器錯誤|  
|503|已到達伺服器容量|  
  
##  <a name="sendrequest"></a>CHttpFile::SendRequest  
 呼叫此成員函式可將要求傳送至 HTTP 伺服器。  
  
```  
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLen = 0,  
    LPVOID lpOptional = NULL,  
    DWORD dwOptionalLen = 0);

 
BOOL SendRequest(
    CString& strHeaders,  
    LPVOID lpOptional = NULL,  
    DWORD dwOptionalLen = 0);
```  
  
### <a name="parameters"></a>參數  
 `pstrHeaders`  
 包含要傳送的標頭名稱的字串指標。  
  
 `dwHeadersLen`  
 所識別的標頭的長度`pstrHeaders`。  
  
 `lpOptional`  
 要求標頭後立即傳送任何選擇性資料。 這通常用於**POST**和**放**作業。 這可以是**NULL**如果沒有要傳送的選擇性資料。  
  
 *dwOptionalLen*  
 `lpOptional` 的長度。  
  
 `strHeaders`  
 字串，包含要傳送的要求標頭的名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx  
 呼叫此成員函式可將要求傳送至 HTTP 伺服器。  
  
```  
BOOL SendRequestEx(
    DWORD dwTotalLen,  
    DWORD dwFlags = HSR_INITIATE,  
    DWORD_PTR dwContext = 1);

 
BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,  
    LPINTERNET_BUFFERS lpBuffOut,  
    DWORD dwFlags = HSR_INITIATE,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 *dwTotalLen*  
 若要在要求中傳送的位元組數目。  
  
 `dwFlags`  
 描述作業的旗標。 如需適當的旗標的清單，請參閱[HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) Windows SDK 中。  
  
 `dwContext`  
 內容識別項`CHttpFile`作業。 此參數的相關資訊，請參閱 < 備註 >。  
  
 `lpBuffIn`  
 指標初始化[INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132)描述用於作業的輸入的緩衝區。  
  
 *lpBuffOut*  
 指標初始化**INTERNET_BUFFERS**描述用於作業的輸出緩衝區。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 此函式可讓您的應用程式使用來傳送資料[寫入](../../mfc/reference/cinternetfile-class.md#write)和[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。 您必須知道要呼叫此函式的其中一個覆寫之前傳送的資料長度。 第一個覆寫可讓您指定您想要傳送的資料長度。 第二個覆寫接受指標**INTERNET_BUFFERS**結構，可以用來描述中有詳細的緩衝區。  
  
 內容寫入至檔案之後，請呼叫[EndRequest](#endrequest)結束作業。  
  
 預設值為`dwContext`MFC 所傳送的`CHttpFile`物件從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md)建構`CHttpFile`物件，您可以覆寫預設值，您選擇的值來設定內容識別碼。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供其所識別的物件上的狀態。 請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
### <a name="example"></a>範例  
 此程式碼片段會將字串的內容傳送至名為 MFCISAPI DLL。本機主機伺服器上的 DLL。 雖然這個範例會使用只有一個呼叫`WriteString`，便傳送資料區塊中使用多個呼叫。  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)

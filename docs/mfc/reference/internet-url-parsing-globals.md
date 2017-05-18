---
title: "網際網路 URL 剖析全域和 Helper |Microsoft 文件"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
caps.latest.revision: 14
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
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: 947ef992d58895e4638d9ffe77fca973cea8eada
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="internet-url-parsing-globals-and-helpers"></a>網際網路 URL 剖析全域和 Helper
當用戶端將查詢傳送至網際網路伺服器時，您可以使用其中一個 URL 剖析全域來擷取用戶端的相關資訊。 Helper 函式會提供其他的網際網路功能。
  
## <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域  
  
|||  
|-|-|  
|[AfxParseURL](#afxparseurl)|剖析 URL 字串並傳回服務類型及其元件。|  
|[AfxParseURLEx](#afxparseurlex)|剖析 URL 字串並傳回服務類型及其元件，並提供使用者名稱和密碼。|  

## <a name="other-internet-helpers"></a>其他網際網路協助程式
|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|擲回例外狀況相關的網際網路連線。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|判斷網際網路控制代碼的類型。|
  
##  <a name="afxparseurl"></a>AfxParseURL  
 此全域用於[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
```   
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort); 
```  
  
### <a name="parameters"></a>參數  
 *pstrURL*  
 包含要剖析 URL 字串的指標。  
  
 `dwServiceType`  
 表示網際網路服務的型別。 可能的值如下：  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 下列服務類型 URL 的第一個區段。  
  
 `strObject`  
 URL 參考的物件 （可能是空的）。  
  
 `nPort`  
 若其中一種由 URL 的伺服器或物件部分。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功剖析 URL;否則，0，表示它是空的或不包含已知的網際網路服務類型。  
  
### <a name="remarks"></a>備註  
 它會剖析 URL 字串，並傳回服務類型及其元件。  
  
 例如，`AfxParseURL`剖析表單的 Url **service://server/dir/dir/object.ext:port**並傳回其元件儲存，如下所示︰  
  
 `strServer`= ="server"  
  
 `strObject`= ="/ dir/dir/object/object.ext"  
  
 `nPort`= = #port  
  
 `dwServiceType`= = #service  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  
  
### <a name="requirements"></a>需求  
  **標頭**afxinet.h  
  
##  <a name="afxparseurlex"></a>AfxParseURLEx  
 此全域函式是擴充的版本[AfxParseURL](#afxparseurl)而且會用於[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
```   
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort,  
    CString& strUsername,  
    CString& strPassword,  
    DWORD dwFlags = 0); 
```  
  
### <a name="parameters"></a>參數  
 *pstrURL*  
 包含要剖析 URL 字串的指標。  
  
 `dwServiceType`  
 表示網際網路服務的型別。 可能的值如下：  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 下列服務類型 URL 的第一個區段。  
  
 `strObject`  
 URL 參考的物件 （可能是空的）。  
  
 `nPort`  
 若其中一種由 URL 的伺服器或物件部分。  
  
 *strUsername*  
 若要參考`CString`物件，其中包含的使用者名稱。  
  
 `strPassword`  
 若要參考`CString`物件，其中包含使用者的密碼。  
  
 `dwFlags`  
 旗標，控制如何剖析的 URL。 可以是下列值的組合︰  
  
|值|意義|  
|-----------|-------------|  
|**ICU_DECODE**|將 %xx 逸出序列轉換為字元。|  
|**ICU_NO_ENCODE**|不會轉換 unsafe 字元來逸出序列。|  
|**ICU_NO_META**|請勿移除中繼序列 （例如"\"。 和"\."）從 URL。|  
|**ICU_ENCODE_SPACES_ONLY**|編碼只空格。|  
|**ICU_BROWSER_MODE**|無法編碼或解碼字元之後 '#' 或 '，而不會移除尾端空白字元之後 '。 如果未指定此值，會編碼整個 URL，並移除尾端空白字元。|  
  
 如果您使用 MFC 的預設值，也就是沒有旗標，函式將所有 unsafe 字元和中繼順序 (例如\\。，\..，和\\...) 來逸出序列。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功剖析 URL;否則，0，表示它是空的或不包含已知的網際網路服務類型。  
  
### <a name="remarks"></a>備註  
 它會剖析 URL 字串，並傳回服務和元件，以及提供使用者名稱和密碼的類型。 旗標會指出如何 unsafe 字元處理。  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  

### <a name="requirements"></a>需求  
  **標頭**afxinet.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
 
## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType
您可以使用此全域函式來判斷網際網路控制代碼的類型。  
   
### <a name="syntax"></a>語法  
  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );  
```
### <a name="parameters"></a>參數  
 `hQuery`  
 網際網路查詢控制代碼。  
   
### <a name="return-value"></a>傳回值  
 任何 WININET 所定義的網際網路服務類型。H. 請參閱 < 備註 > 一節如需這些網際網路服務。 如果控制代碼為 NULL，或無法辨識，函數會傳回 AFX_INET_SERVICE_UNK。  
   
### <a name="remarks"></a>備註  
 下列清單包含所傳回的可能網際網路類型`AfxGetInternetHandleType`。  
  
-   INTERNET_HANDLE_TYPE_INTERNET  
  
-   INTERNET_HANDLE_TYPE_CONNECT_FTP  
  
-   INTERNET_HANDLE_TYPE_CONNECT_GOPHER  
  
-   INTERNET_HANDLE_TYPE_CONNECT_HTTP  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_HTTP_REQUEST  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  
   
### <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
 
## <a name="afxthrowinternetexception"></a>AfxThrowInternetException
網際網路例外狀況會擲回。  
   
### <a name="syntax"></a>語法    
```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );  
```
### <a name="parameters"></a>參數  
 `dwContext`  
 造成錯誤的作業內容識別碼。 預設值`dwContext`中原本指定[CInternetSession](cinternetsession-class.md)並傳遞給[CInternetConnection](cinternetconnection-class.md)-和[CInternetFile](cinternetfile-class.md)-衍生的類別。 針對特定連接或將檔案上執行的作業，您通常覆寫預設`dwContext`您自己。 此值則會傳回至[CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback)來識別特定作業的狀態。 
  
 `dwError`  
 造成例外狀況時發生錯誤。  
   
### <a name="remarks"></a>備註  
 您有責任判斷基礎的作業系統錯誤碼的原因。  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  
   
### <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [CInternetException 類別](cinternetexception-class.md)   
 [擲回](#throw)
 



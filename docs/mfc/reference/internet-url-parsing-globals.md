---
title: "網際網路 URL 剖析全域 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 3aec259acae2f5e9c9b65ac4e5c898ca57ff3d52
ms.lasthandoff: 02/24/2017

---
# <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域
當用戶端將查詢傳送至網際網路伺服器時，您可以使用其中一個 URL 剖析全域來擷取用戶端的相關資訊。  
  
### <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域  
  
|||  
|-|-|  
|[AfxParseURL](#afxparseurl)|剖析 URL 字串並傳回服務類型及其元件。|  
|[AfxParseURLEx](#afxparseurlex)|剖析 URL 字串並傳回服務類型及其元件，並提供使用者名稱和密碼。|  
  
##  <a name="a-nameafxparseurla--afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL  
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
 包含要剖析 URL 的字串指標。  
  
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
 URL 參考的物件 （可能為空白）。  
  
 `nPort`  
 如果是的話，從伺服器或物件的 url 部分決定。  
  
### <a name="return-value"></a>傳回值  
 已成功剖析 URL; 如果為非零如果它是空的或不包含已知的網際網路服務型別，否則為 0。  
  
### <a name="remarks"></a>備註  
 它會剖析 URL 字串並傳回服務及其元件的類型。  
  
 例如，`AfxParseURL`剖析 Url 格式的**service://server/dir/dir/object.ext:port** ，並傳回其元件儲存，如下所示︰  
  
 `strServer`= ="server"  
  
 `strObject`= ="/ dir/dir/object/object.ext 」  
  
 `nPort`= = #port  
  
 `dwServiceType`= = #service  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  
  
### <a name="requirements"></a>需求  
  **標頭**afxinet.h  
  
##  <a name="a-nameafxparseurlexa--afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx  
 此全域函式是擴充的版本[AfxParseURL](#afxparseurl) ，並用於[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
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
 包含要剖析 URL 的字串指標。  
  
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
 URL 參考的物件 （可能為空白）。  
  
 `nPort`  
 如果是的話，從伺服器或物件的 url 部分決定。  
  
 *strUsername*  
 參考`CString`物件，其中包含的使用者名稱。  
  
 `strPassword`  
 參考`CString`物件，其中包含使用者的密碼。  
  
 `dwFlags`  
 旗標，控制如何剖析的 URL。 可以是下列值的組合︰  
  
|值|意義|  
|-----------|-------------|  
|**ICU_DECODE**|將 %xx 逸出序列轉換成字元。|  
|**ICU_NO_ENCODE**|不轉換不安全的字元逸出序列。|  
|**ICU_NO_META**|請勿移除中繼序列 （例如"\"。 和"\."）從 URL。|  
|**ICU_ENCODE_SPACES_ONLY**|編碼只空格。|  
|**ICU_BROWSER_MODE**|無法編碼或解碼字元之後 '#' 或 '，但請勿移除尾端空白之後 '。 如果未指定此值，整個 URL 編碼，並移除尾端空白字元。|  
  
 如果您使用 MFC 的預設值，也就是沒有旗標，函數將所有 unsafe 字元和中繼順序 (例如\\。，\...，和\\...) 來逸出序列。  
  
### <a name="return-value"></a>傳回值  
 已成功剖析 URL; 如果為非零如果它是空的或不包含已知的網際網路服務型別，否則為 0。  
  
### <a name="remarks"></a>備註  
 它會剖析 URL 字串，並傳回服務及其元件，以及提供使用者名稱和密碼的類型。 旗標會指出如何 unsafe 字元處理。  
  
> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET。H.  

### <a name="requirements"></a>需求  
  **標頭**afxinet.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)


---
title: CInternetConnection 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
dev_langs:
- C++
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07b269afce3ec0c3ef60e6cc37782fdea18260cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cinternetconnection-class"></a>CInternetConnection 類別
管理您與網際網路伺服器的連接。  
  
## <a name="syntax"></a>語法  
  
```  
class CInternetConnection : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetConnection::CInternetConnection](#cinternetconnection)|建構 `CInternetConnection` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetConnection::GetContext](#getcontext)|取得此連接物件的內容識別碼。|  
|[CInternetConnection::GetServerName](#getservername)|取得與連接相關聯的伺服器名稱。|  
|[CInternetConnection::GetSession](#getsession)|取得指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)與連接相關聯的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|網際網路工作階段控制代碼。|  
  
## <a name="remarks"></a>備註  
 它是 MFC 類別的基底類別[CFtpConnection](../../mfc/reference/cftpconnection-class.md)， [CHttpConnection](../../mfc/reference/chttpconnection-class.md)，和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。 每個類別會提供額外的功能與個別的 FTP、 HTTP 或 gopher 伺服器進行通訊。  
  
 若要直接與網際網路伺服器通訊，您必須擁有[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件和`CInternetConnection`物件。  
  
 若要了解有關 WinInet 類別如何工作的詳細資訊，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection  
 此成員函式時，會呼叫`CInternetConnection`建立物件。  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>參數  
 `pSession`  
 指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。  
  
 `pstrServer`  
 包含伺服器名稱的字串指標。  
  
 `nPort`  
 識別此連線的網際網路連接埠號碼。  
  
 `dwContext`  
 內容識別項`CInternetConnection`物件。 請參閱**備註**如需有關`dwContext`。  
  
### <a name="remarks"></a>備註  
 您永遠不會呼叫`CInternetConnection`自行; 請改為呼叫[CInternetSession](../../mfc/reference/cinternetsession-class.md)您想要建立的連線類型的成員函式：  
  
- [Cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 預設值為`dwContext`MFC 所傳送的`CInternetConnection`-衍生物件從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立**InternetConnection**-衍生物件。 預設是設為 1。不過，您可以明確指派的特定內容識別元[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)建構函式連接。 物件，且任何工作，它會將相關聯的內容識別碼。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供其所識別的物件上的狀態。 請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別碼。  
  
##  <a name="getcontext"></a>  CInternetConnection::GetContext  
 呼叫此成員函式可取得這個工作階段的內容識別碼。  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>傳回值  
 應用程式指派的內容識別碼。  
  
### <a name="remarks"></a>備註  
 中原本指定的內容識別碼[CInternetSession](../../mfc/reference/cinternetsession-class.md)並將傳播到`CInternetConnection`-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)-衍生的類別，除非以不同的方式開啟函式呼叫中指定連接。 內容識別碼是否與指定之任何的物件作業相關聯，以及識別傳回作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
 如需有關如何**GetContext**可搭配其他 WinInet 類別，以提供的使用者狀態資訊，請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)如需有關內容識別項。  
  
##  <a name="getservername"></a>  CInternetConnection::GetServerName  
 呼叫此成員函式可取得與此網際網路連線相關聯的伺服器名稱。  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用此連接物件的伺服器名稱。  
  
##  <a name="getsession"></a>  CInternetConnection::GetSession  
 呼叫此成員函式取得的指標`CInternetSession`與此連線相關聯的物件。  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)網際網路連線物件相關聯的物件。  
  
##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET  
 您可以使用這個運算子來取得目前的網際網路工作階段的應用程式開發介面層級的控制代碼。  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




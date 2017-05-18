---
title: "CSocketAddr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 19
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
ms.openlocfilehash: ee3f69874460d09e495a237985a98ace19134a01
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="csocketaddr-class"></a>CSocketAddr 類別
這個類別會提供主機名稱轉換成主機位址，支援 IPv4 和 IPV6 格式的方法。  
  
## <a name="syntax"></a>語法  
  
```
class CSocketAddr
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSocketAddr::CSocketAddr](#csocketaddr)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSocketAddr::FindAddr](#findaddr)|呼叫此方法以提供的主機名稱轉換成主機位址。|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|呼叫這個方法將 IPv4 主機名稱的主機位址。|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|呼叫這個方法，以轉換成 IPv6 主機名稱的主機位址。|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|呼叫此方法以傳回中特定元素的指標**addrinfo**清單。|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|呼叫這個方法傳回的指標**addrinfo**清單。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供 IP 版本無從驗證的方法，來查閱與 Windows 搭配使用的網路位址的通訊端 API 函式和程式庫中的通訊端包裝函式。  
  
 這個類別的成員，顯示用來查詢網路位址使用 Win32 API 函式[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)。  
  
 這個類別支援兩個 IPv4 andIPv6 網路位址。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsocket.h  
  
##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 建構函式。  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>備註  
 建立新`CSocketAddr`物件，並初始化包含主機的回應資訊的連結的清單。  
  
##  <a name="findaddr"></a>CSocketAddr::FindAddr  
 呼叫此方法以提供的主機名稱轉換成主機位址。  
  
```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```  
  
### <a name="parameters"></a>參數  
 `szHost`  
 主機名稱或點線的 IP 位址。  
  
 *szPortOrServiceName*  
 連接埠號碼或主機上的服務名稱。  
  
 `nPortNo`  
 連接埠號碼。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的組合。  
  
 *addr_family*  
 位址 （例如 PF_INET)。  
  
 `sock_type`  
 通訊端類型 （例如 SOCK_STREAM)。  
  
 *ai_proto*  
 通訊協定 （例如 IPPROTO_IP 或 IPPROTO_IPV6）。  
  
### <a name="return-value"></a>傳回值  
 如果成功計算出的位址，則傳回零。 傳回非零的 Windows 通訊端錯誤程式碼失敗。 如果成功，導出的位址會儲存在連結清單可能會使用參考`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>備註  
 主機名稱參數可能是 IPv4 或 IPv6 格式。 這個方法會呼叫 Win32 API 函式[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)來執行轉換。  
  
##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
 呼叫這個方法將 IPv4 主機名稱的主機位址。  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>參數  
 `szHost`  
 主機名稱或點線的 IP 位址。  
  
 `nPortNo`  
 連接埠號碼。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的組合。  
  
 `sock_type`  
 通訊端類型 （例如 SOCK_STREAM)。  
  
### <a name="return-value"></a>傳回值  
 如果成功計算出的位址，則傳回零。 傳回非零的 Windows 通訊端錯誤程式碼失敗。 如果成功，導出的位址會儲存在連結清單可能會使用參考`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 Win32 API 函式[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)來執行轉換。  
  
##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 呼叫這個方法，以轉換成 IPv6 主機名稱的主機位址。  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>參數  
 `szHost`  
 主機名稱或點線的 IP 位址。  
  
 `nPortNo`  
 連接埠號碼。  
  
 `flags`  
 0 或 AI_PASSIVE、 AI_CANONNAME 或 AI_NUMERICHOST 的組合。  
  
 `sock_type`  
 通訊端類型 （例如 SOCK_STREAM)。  
  
### <a name="return-value"></a>傳回值  
 如果成功計算出的位址，則傳回零。 傳回非零的 Windows 通訊端錯誤程式碼失敗。 如果成功，導出的位址會儲存在連結清單可能會使用參考`CSocketAddr::GetAddrInfoList`和`CSocketAddr::GetAddrInfo`。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫 Win32 API 函式[getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)來執行轉換。  
  
##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 呼叫此方法以傳回中特定元素的指標**addrinfo**清單。  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 中特定元素的參考[addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530)清單。  
  
### <a name="return-value"></a>傳回值  
 傳回的指標**addrinfo**所參考的結構`nIndex`包含主機的回應資訊的連結清單中。  
  
##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 呼叫這個方法傳回的指標**addrinfo**清單。  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>傳回值  
 一或多個連結清單指向`addrinfo`結構，其中包含主機的回應資訊。 如需詳細資訊`addrinfo`結構時，請參閱 「 addrinfo 」 文件中的[MSDN 文件庫](http://go.microsoft.com/fwlink/linkid=556)  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)


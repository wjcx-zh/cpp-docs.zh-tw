---
title: CSocketAddr 類別
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496338"
---
# <a name="csocketaddr-class"></a>CSocketAddr 類別

此類別提供將主機名稱轉換成主機位址的方法, 同時支援 IPv4 和 IPV6 格式。

## <a name="syntax"></a>語法

```
class CSocketAddr
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|呼叫這個方法, 將提供的主機名稱轉換成主機位址。|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|呼叫這個方法, 將 IPv4 主機名稱轉換成主機位址。|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|呼叫這個方法, 將 IPv6 主機名稱轉換成主機位址。|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|呼叫這個方法, 以傳回`addrinfo`清單中特定元素的指標。|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|呼叫這個方法, 以傳回`addrinfo`清單的指標。|

## <a name="remarks"></a>備註

此類別提供一種 IP 版本無關的方法, 用來查閱網路位址以用於程式庫中的 Windows 通訊端 API 函式和通訊端包裝函式。

此類別用來查閱網路位址的成員會使用 WIN32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)。 系統會根據您的程式碼是否針對 ANSI 或 UNICODE 進行編譯, 來呼叫函式的 ANSI 或 UNICODE 版本。

此類別支援兩個 IPv4 andIPv6 網路位址。

## <a name="requirements"></a>需求

**標頭:** atlsocket。h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

建構函式。

```
CSocketAddr();
```

### <a name="remarks"></a>備註

建立新`CSocketAddr`的物件, 並初始化包含主機回應資訊的連結清單。

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

呼叫這個方法, 將提供的主機名稱轉換成主機位址。

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>參數

*szHost*<br/>
主機名稱或點的 IP 位址。

*szPortOrServiceName*<br/>
主機上的服務埠編號或名稱。

*nPortNo*<br/>
埠號碼。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的組合。

*addr_family*<br/>
位址系列 (例如 PF_INET)。

*sock_type*<br/>
通訊端類型 (例如 SOCK_STREAM)。

*ai_proto*<br/>
通訊協定 (例如 IPPROTO_IP 或 IPPROTO_IPV6)。

### <a name="return-value"></a>傳回值

如果已成功計算位址, 則傳回零。 失敗時傳回非零的 Windows 通訊端錯誤碼。 如果成功, 則會將匯出的位址儲存在連結的清單中, 而且`CSocketAddr::GetAddrInfoList`可以`CSocketAddr::GetAddrInfo`使用和來參考。

### <a name="remarks"></a>備註

主機名稱參數可以是 IPv4 或 IPv6 格式。 這個方法會呼叫 WIN32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

呼叫這個方法, 將 IPv4 主機名稱轉換成主機位址。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>參數

*szHost*<br/>
主機名稱或點的 IP 位址。

*nPortNo*<br/>
埠號碼。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的組合。

*sock_type*<br/>
通訊端類型 (例如 SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果已成功計算位址, 則傳回零。 失敗時傳回非零的 Windows 通訊端錯誤碼。 如果成功, 則會將匯出的位址儲存在連結的清單中, 而且`CSocketAddr::GetAddrInfoList`可以`CSocketAddr::GetAddrInfo`使用和來參考。

### <a name="remarks"></a>備註

這個方法會呼叫 WIN32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

呼叫這個方法, 將 IPv6 主機名稱轉換成主機位址。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>參數

*szHost*<br/>
主機名稱或點的 IP 位址。

*nPortNo*<br/>
埠號碼。

*flags*<br/>
0或 AI_PASSIVE、AI_CANONNAME 或 AI_NUMERICHOST 的組合。

*sock_type*<br/>
通訊端類型 (例如 SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果已成功計算位址, 則傳回零。 失敗時傳回非零的 Windows 通訊端錯誤碼。 如果成功, 則會將匯出的位址儲存在連結的清單中, 而且`CSocketAddr::GetAddrInfoList`可以`CSocketAddr::GetAddrInfo`使用和來參考。

### <a name="remarks"></a>備註

這個方法會呼叫 WIN32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

呼叫這個方法, 以傳回`addrinfo`清單中特定元素的指標。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[Addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow)清單中特定元素的參考。

### <a name="return-value"></a>傳回值

傳回連結清單中`addrinfo` *nIndex*所參考結構的指標, 其中包含主機的回應資訊。

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

呼叫這個方法, 以傳回`addrinfo`清單的指標。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>傳回值

包含主機回應資訊的一或多個`addrinfo`結構之連結清單的指標。 如需詳細資訊, 請參閱[addrinfo 結構](/windows/win32/api/ws2def/ns-ws2def-addrinfow)。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)

---
title: 克塞底載入器類
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
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330686"
---
# <a name="csocketaddr-class"></a>克塞底載入器類

此類提供了將主機名轉換為主機位址的方法,支援IPv4和IPV6格式。

## <a name="syntax"></a>語法

```
class CSocketAddr
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Socket::socket](#csocketaddr)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Socket::尋找新增器](#findaddr)|調用此方法可將提供的主機名轉換為主機位址。|
|[Socket::尋找 INET4Addr](#findinet4addr)|調用此方法將 IPv4 主機名轉換為主機位址。|
|[Socket::尋找 INET6Addr](#findinet6addr)|調用此方法將 IPv6 主機名轉換為主機位址。|
|[CSocketAddr:取得AddrInfo](#getaddrinfo)|呼叫此方法以返回指向清單中特定元素的`addrinfo`指標。|
|[Socket::取得AddrInfoList](#getaddrinfolist)|呼叫此方法以返回指向清單的`addrinfo`指標。|

## <a name="remarks"></a>備註

此類提供了一種與IP版本無關的方法,用於查找網路位址,以便與庫中的Windows套接字API函數和套接字包裝器配合使用。

此成員用於尋找網路位址,使用 Win32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)。 根據代碼是為 ANSI 還是 UNICODE 編譯的,調用該函數的 ANSI 或 UNICODE 版本。

此類同時支援 IPv4 和 IPv6 網路位址。

## <a name="requirements"></a>需求

**標題:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>Socket::socket

建構函式。

```
CSocketAddr();
```

### <a name="remarks"></a>備註

建立新`CSocketAddr`物件並初始化包含有關主機的回應資訊的連結清單。

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>Socket::尋找新增器

調用此方法可將提供的主機名轉換為主機位址。

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
主機名或虛點 IP 位址。

*szPortOr服務名稱*<br/>
主機上的埠號或服務名稱。

*n波特諾*<br/>
連接埠號碼。

*標誌*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的組合。

*addr_family*<br/>
位址族(如PF_INET)。

*sock_type*<br/>
套接字類型(如SOCK_STREAM)。

*ai_proto*<br/>
協定(如IPPROTO_IP或IPPROTO_IPV6)。

### <a name="return-value"></a>傳回值

如果位址計算成功,則返回零。 在發生故障時返回非零 Windows 套接字錯誤代碼。 如果成功,計算的位址將存儲在連結`CSocketAddr::GetAddrInfoList`清單中,該清單可以使用`CSocketAddr::GetAddrInfo`和引用。

### <a name="remarks"></a>備註

主機名參數可能採用 IPv4 或 IPv6 格式。 此方法調用 Win32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>Socket::尋找 INET4Addr

調用此方法將 IPv4 主機名轉換為主機位址。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>參數

*szHost*<br/>
主機名或虛點 IP 位址。

*n波特諾*<br/>
連接埠號碼。

*標誌*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的組合。

*sock_type*<br/>
套接字類型(如SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果位址計算成功,則返回零。 在發生故障時返回非零 Windows 套接字錯誤代碼。 如果成功,計算的位址將存儲在連結`CSocketAddr::GetAddrInfoList`清單中,該清單可以使用`CSocketAddr::GetAddrInfo`和引用。

### <a name="remarks"></a>備註

此方法調用 Win32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>Socket::尋找 INET6Addr

調用此方法將 IPv6 主機名轉換為主機位址。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>參數

*szHost*<br/>
主機名或虛點 IP 位址。

*n波特諾*<br/>
連接埠號碼。

*標誌*<br/>
0 或AI_PASSIVE、AI_CANONNAME或AI_NUMERICHOST的組合。

*sock_type*<br/>
套接字類型(如SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果位址計算成功,則返回零。 在發生故障時返回非零 Windows 套接字錯誤代碼。 如果成功,計算的位址將存儲在連結`CSocketAddr::GetAddrInfoList`清單中,該清單可以使用`CSocketAddr::GetAddrInfo`和引用。

### <a name="remarks"></a>備註

此方法調用 Win32 API 函數[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)來執行轉換。

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr:取得AddrInfo

呼叫此方法以返回指向清單中特定元素的`addrinfo`指標。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
對[addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow)清單中特定元素的引用。

### <a name="return-value"></a>傳回值

返回指向連結清單中`addrinfo`*nIndex*引用的結構的指標,其中包含有關主機的回應資訊。

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>Socket::取得AddrInfoList

呼叫此方法以返回指向清單的`addrinfo`指標。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>傳回值

指向包含有關主機的回應資訊的一`addrinfo`個或多個結構的連結清單。 有關詳細資訊,請參閱[addrinfo 結構](/windows/win32/api/ws2def/ns-ws2def-addrinfow)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

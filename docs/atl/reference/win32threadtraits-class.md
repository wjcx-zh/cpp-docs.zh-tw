---
title: Win32ThreadTraits 類別
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495467"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 類別

這個類別會提供 Windows 執行緒的建立函式。 如果執行緒不會使用 CRT 函式, 請使用這個類別。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class Win32ThreadTraits
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|靜止呼叫此函式可建立不應使用 CRT 函式的執行緒。|

## <a name="remarks"></a>備註

執行緒特性是針對特定的執行緒類型提供建立函式的類別。 建立函式的簽章和語義與 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函數相同。

執行緒特性由下列類別使用:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果執行緒將使用 CRT 函式, 請改用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 。

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="createthread"></a>Win32ThreadTraits:: CreateThread

呼叫此函式可建立不應使用 CRT 函式的執行緒。

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>參數

*lpsa*<br/>
新執行緒的安全性屬性。

*dwStackSize*<br/>
新執行緒的堆疊大小。

*pfnThreadProc*<br/>
新執行緒的執行緒程式。

*pvParam*<br/>
要傳遞至執行緒程式的參數。

*dwCreationFlags*<br/>
建立旗標 (0 或 CREATE_SUSPENDED)。

*pdwThreadId*<br/>
脫銷DWORD 變數的位址, 在成功時, 會接收新建立執行緒的執行緒識別碼。

### <a name="return-value"></a>傳回值

將控制碼傳回至新建立的執行緒, 或在失敗時傳回 Null。 呼叫[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以取得擴充的錯誤資訊。

### <a name="remarks"></a>備註

如需此函式之參數的進一步資訊, 請參閱[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 。

這個函數會`CreateThread`呼叫來建立執行緒。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)

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
ms.openlocfilehash: da4b8b3d5a41ab16dc2027fd632c56158afd3b97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275934"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 類別

這個類別會提供以 Windows 執行緒的建立函式。 如果執行緒不會使用 CRT 函式，請使用這個類別。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class Win32ThreadTraits
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|（靜態）呼叫此函式來建立不應使用 CRT 函式的執行緒。|

## <a name="remarks"></a>備註

執行緒的特性是執行緒的提供特定類型建立函式的類別。 為 Windows 建立函式具有相同的簽章和語意[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)函式。

下列類別會使用執行緒的特性：

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果執行緒將會使用 CRT 函式，使用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)改。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

呼叫此函式來建立不應使用 CRT 函式的執行緒。

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
新的執行緒安全性屬性。

*dwStackSize*<br/>
新的執行緒堆疊大小。

*pfnThreadProc*<br/>
新執行緒的執行緒程序。

*pvParam*<br/>
要傳遞至執行緒程序的參數。

*dwCreationFlags*<br/>
建立旗標 （0 或 CREATE_SUSPENDED）。

*pdwThreadId*<br/>
[out]變數的位址 DWORD，成功時，接收新建立的執行緒的執行緒識別碼。

### <a name="return-value"></a>傳回值

傳回新建立的執行緒或 NULL 的控制代碼，在失敗。 呼叫[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)若要取得延伸錯誤資訊。

### <a name="remarks"></a>備註

請參閱[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)更多有關此函數的參數。

此函式會呼叫`CreateThread`建立執行緒。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

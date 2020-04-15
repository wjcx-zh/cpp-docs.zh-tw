---
title: CRTThreadtraits 類別
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: a7cfddc64e8c1b4e192e718d05812e385fbe08ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331018"
---
# <a name="crtthreadtraits-class"></a>CRTThreadtraits 類別

此類提供 CRT 線程的創建函數。 如果執行緒將使用 CRT 函數,請使用此類。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CRTThreadTraits
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRTThreadtraits:建立執行緒](#createthread)|(靜態)呼叫此函數以建立可以使用 CRT 函數的線程。|

## <a name="remarks"></a>備註

線程特徵是為特定類型的線程提供創建函數的類。 創建函數具有與 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函數相同的簽名和語義。

執行緒特徵由以下類別使用:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果線程不使用 CRT 函數,請使用[Win32ThreadTraits。](../../atl/reference/win32threadtraits-class.md)

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadtraits:建立執行緒

呼叫此函數以建立可以使用 CRT 函數的線程。

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
新線程的安全屬性。

*dwStackSize*<br/>
新線程的堆疊大小。

*普芬線程普羅克*<br/>
新線程的線程過程。

*pvParam*<br/>
要傳遞給線程過程的參數。

*dw創造標誌*<br/>
創建標誌(0 或CREATE_SUSPENDED)。

*pdwThreadId*<br/>
[出]DWORD 變數的位址,在成功時,接收新創建的線程的線程 ID。

### <a name="return-value"></a>傳回值

將句柄傳回到新建立的線程或失敗時為 NULL。 調用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)獲取擴充的錯誤資訊。

### <a name="remarks"></a>備註

有關此函數的參數的詳細資訊,請參閱[CreateThread。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

此函數調用[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)以創建線程。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

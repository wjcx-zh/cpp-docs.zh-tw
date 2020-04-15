---
title: _endthread、_endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348042"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

終止線程;**_endthread**終止**由_beginthread**創建的線程 **,_endthreadex**終止由 **_beginthreadex**創建的線程。

## <a name="syntax"></a>語法

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>參數

*retval*<br/>
執行緒結束代碼。

## <a name="remarks"></a>備註

您可以顯式調用 **_endthread**或 **_endthreadex**以終止線程;否則,您可以顯式調用線程。但是,當線程從作為參數傳遞的例程**返回_beginthread或****_beginthreadex**時,將自動調用 **_endthread**或 **_endthreadex。** 終止線程與調用**端線程**或 **_endthreadex**有助於確保正確恢復分配給線程的資源。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 **_endthread****和_endthreadex**回收分配的線程資源,然後呼叫**ExitThread**。

**_endthread**自動關閉線程句柄。 (此行為不同於 Win32**退出線程**API。因此,當您使用 **_beginthread**和 **_endthread**時,不要通過調用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 顯式關閉線程句柄。

與 Win32 **ExitThread** API 一樣 **,_endthreadex**不會關閉線程句柄。 因此,當您使用 **_beginthreadex**和 **_endthreadex**時,必須通過調用 Win32 **CloseHandle** API 來關閉線程句柄。

> [!NOTE]
> **_endthread**和 **_endthreadex**會導致線程中掛起的C++析構函數不調用。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

## <a name="example"></a>範例

請參閱 [_beginthread](beginthread-beginthreadex.md) 的範例。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>

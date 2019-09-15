---
title: _endthread、_endthreadex
ms.date: 11/04/2016
api_name:
- _endthread
- _endthreadex
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
ms.openlocfilehash: c9dd4a49e534e8fa3e0f5ac735faccb4b0f65af5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937738"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

終止執行緒; **_endthread**會終止由 **_beginthread**建立的執行緒，而 **_endthreadex**會終止由 **_beginthreadex**所建立的執行緒。

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

您可以明確地呼叫 **_endthread**或 **_endthreadex**來終止執行緒;不過，當執行緒從做為參數傳遞至 **_beginthread**或 **_beginthreadex**的常式返回時，會自動呼叫 **_endthread**或 **_endthreadex** 。 透過呼叫**endthread**或 **_endthreadex**來終止執行緒，有助於確保適當復原配置給執行緒的資源。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 **_endthread**和 **_endthreadex**會回收配置的執行緒資源，然後呼叫**ExitThread**。

**_endthread**會自動關閉執行緒控制碼。 （此行為與 Win32 **ExitThread** API 不同）。因此，當您使用 **_beginthread**和 **_endthread**時，請不要藉由呼叫 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 來明確關閉執行緒控制碼。

如同 Win32 **ExitThread** API， **_endthreadex**不會關閉執行緒控制碼。 因此，當您使用 **_beginthreadex**和 **_endthreadex**時，您必須藉由呼叫 Win32 **CloseHandle** API 來關閉執行緒控制碼。

> [!NOTE]
> **_endthread**和 **_endthreadex**會C++導致不會呼叫執行緒中暫止的析構函數。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

## <a name="example"></a>範例

請參閱 [_beginthread](beginthread-beginthreadex.md)的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>

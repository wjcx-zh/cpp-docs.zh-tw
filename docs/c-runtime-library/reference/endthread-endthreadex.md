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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a3889adcc90bd62e766102b72aae68577915e55b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915076"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

終止執行緒;**_endthread**終止由 **_beginthread**所建立的執行緒， **_endthreadex**終止由 **_beginthreadex**所建立的執行緒。

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

您可以呼叫 **_endthread**或明確地 **_endthreadex**以終止執行緒;不過，當執行緒從做為參數傳遞至 **_beginthread**或 **_beginthreadex**的常式返回時，會自動呼叫 **_endthread**或 **_endthreadex** 。 使用**endthread**或 **_endthreadex**的呼叫來終止執行緒，有助於確保適當復原配置給執行緒的資源。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 **_endthread**和 **_endthreadex**回收已配置的執行緒資源，然後呼叫**ExitThread**。

**_endthread**會自動關閉執行緒控制碼。 （此行為與 Win32 **ExitThread** API 不同）。因此，當您使用 **_beginthread**和 **_endthread**時，請不要藉由呼叫 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 來明確地關閉執行緒控制碼。

如同 Win32 **ExitThread** API， **_endthreadex**不會關閉執行緒控制碼。 因此，當您使用 **_beginthreadex**和 **_endthreadex**時，您必須藉由呼叫 Win32 **CloseHandle** API 來關閉執行緒控制碼。

> [!NOTE]
> **_endthread**和 **_endthreadex**導致不會呼叫執行緒中的 c + + 析構函數暫止。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

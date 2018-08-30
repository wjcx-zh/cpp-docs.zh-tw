---
title: _endthread、_endthreadex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _endthread
- _endthreadex
apilocation:
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
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs:
- C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bed0b93b2c9643a19aa8fd97c0e52da2ba1f8be
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198786"
---
# <a name="endthread-endthreadex"></a>_endthread、_endthreadex

中止執行緒;**_endthread**終止所建立的執行緒 **_beginthread**並 **_endthreadex**中止執行緒所建立的 **_beginthreadex**.

## <a name="syntax"></a>語法

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>參數

*retval*執行緒結束代碼。

## <a name="remarks"></a>備註

您可以呼叫 **_endthread**或 **_endthreadex**明確地終止執行緒; 不過， **_endthread**或是 **_endthreadex**稱為自動從常式的執行緒傳回時做為參數傳遞 **_beginthread**或是 **_beginthreadex**。 結束藉由呼叫執行緒**endthread**或是 **_endthreadex**有助於確保適當復原配置執行緒的資源。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 **_endthread**並 **_endthreadex**回收配置的執行緒資源，然後呼叫**ExitThread**。

**_endthread**會自動關閉執行緒控制代碼。 (此行為不同於 Win32 **ExitThread** API。)因此，當您使用 **_beginthread**並 **_endthread**，不要明確地關閉執行緒控制代碼藉由呼叫 Win32 [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API。

像是 Win32 **ExitThread** API **_endthreadex**不會關閉執行緒控制代碼。 因此，當您使用 **_beginthreadex**並 **_endthreadex**，您必須關閉執行緒控制代碼藉由呼叫 Win32 **CloseHandle** API。

> [!NOTE]
> **_endthread**並 **_endthreadex**暫止的 c + + 解構函式會導致不是要呼叫的執行緒。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md) 的多執行緒版本。

## <a name="example"></a>範例

請參閱 [_beginthread](beginthread-beginthreadex.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>

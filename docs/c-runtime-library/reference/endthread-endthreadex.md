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
ms.openlocfilehash: d4588829b3ec1d348405be925a75c493f4e8594b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="endthread-endthreadex"></a>_endthread、_endthreadex

中止執行緒;**_endthread**中止執行緒所建立的 **_beginthread**和 **_endthreadex**中止執行緒所建立的 **_beginthreadex**.

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

您可以呼叫 **_endthread**或 **_endthreadex**明確來終止執行緒; 然而， **_endthread**或 **_endthreadex**稱為自動從常式的執行緒傳回時當做參數傳遞 **_beginthread**或 **_beginthreadex**。 終止執行緒呼叫**endthread**或 **_endthreadex**有助於確保適當復原配置給執行緒的資源。

> [!NOTE]
> 對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。 **_endthread**和 **_endthreadex**回收配置的執行緒資源，然後呼叫**ExitThread**。

**_endthread**會自動關閉執行緒控制代碼。 (此行為不同於 Win32 **ExitThread** API。)因此，當您使用 **_beginthread**和 **_endthread**，請勿明確地關閉執行緒控制代碼藉由呼叫 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx)應用程式開發介面。

像 Win32 **ExitThread** API， **_endthreadex**不會關閉執行緒控制代碼。 因此，當您使用 **_beginthreadex**和 **_endthreadex**，您必須關閉執行緒控制代碼藉由呼叫 Win32 **CloseHandle**應用程式開發介面。

> [!NOTE]
> **_endthread**和 **_endthreadex**暫止的 c + + 解構函式會導致不是要呼叫的執行緒。

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

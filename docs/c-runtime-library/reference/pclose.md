---
title: _pclose
ms.date: 11/04/2016
apiname:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: eb0f54ec27992cd0e62b11d8fec5bd54c3daea4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156003"
---
# <a name="pclose"></a>_pclose

等候新的命令處理程式，然後關閉相關管道上的資料流。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>參數

*stream*<br/>
從先前的呼叫傳回值 **_popen**。

## <a name="return-value"></a>傳回值

如果發生錯誤，請傳回終止的命令處理，則為-1 的結束狀態。 傳回值的格式是針對相同 **_cwait**，但低序位與高序位位元組會互換。 如果資料流**NULL**， **_pclose**設定**errno**至**EINVAL**並傳回-1。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Pclose**函式會查閱由相關聯的啟動命令處理器 (Cmd.exe) 的處理序識別碼 **_popen**呼叫、 執行[_cwait](cwait.md)呼叫新的命令處理器，然後關閉相關管道上的資料流。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen、_wpopen](popen-wpopen.md)<br/>

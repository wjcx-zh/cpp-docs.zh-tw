---
title: _chdrive
ms.date: 11/04/2016
apiname:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 7e36867bb8237c549fd250be88a99244766920ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500271"
---
# <a name="_chdrive"></a>_chdrive

變更目前工作磁碟機。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>參數

*drive*<br/>
1 到 26 範圍內指定目前工作磁碟機的整數 (1=A、2=B 等)。

## <a name="return-value"></a>傳回值

若已成功變更目前工作磁碟機即為零 (0)；否則為 -1。

## <a name="remarks"></a>備註

如果*磁片磁碟機*不在1到26的範圍內, 則會叫用不正確參數處理常式, 如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, **_chdrive**函數會傳回-1, **errno**會設定為**EACCES**, 而 **_doserrno**會設定為**ERROR_INVALID_DRIVE**。

**_chdrive** 函式不是安全執行緒，原因是其取決於本身不是安全執行緒的 **SetCurrentDirectory** 函式。 若要在多執行緒應用程式中安全地使用 **_chdrive**，您必須提供自己的執行緒同步處理。 如需詳細資訊, 請參閱[SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)。

**_chdrive** 函式只會變更目前工作磁碟機； **_chdir** 則會變更目前工作目錄。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_getdrive](getdrive.md) 的範例。

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>

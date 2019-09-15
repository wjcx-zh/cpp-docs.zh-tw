---
title: _splitpath、_wsplitpath
ms.date: 11/04/2016
api_name:
- _wsplitpath
- _splitpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: a502977faf91d744868c4aef79b3a40ca240a90f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958045"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath、_wsplitpath

將一個路徑名稱分割為多個元件。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

## <a name="syntax"></a>語法

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>參數

*path*<br/>
完整路徑。

*drive*<br/>
磁碟機號，後面接著冒號（ **：** ）。 如果您不需要磁碟機號，您可以為此參數傳遞**Null** 。

*dir*<br/>
目錄路徑，包括結尾斜線。 可以使用正 **/** 斜線（）、 **\\** 反斜線（）或兩者。 如果您不需要目錄路徑，您可以為此參數傳遞**Null** 。

*fname*<br/>
基底檔名 (無副檔名)。 如果您不需要檔案名，可以針對這個參數傳遞**Null** 。

*ext*<br/>
副檔名，包括前置句點（ **.** ）。 如果您不需要副檔名，則可以傳遞此參數的**Null** 。

## <a name="remarks"></a>備註

**_Splitpath**函式會將路徑分割成四個元件。 **_splitpath**會自動將多位元組字元字串引數處理為適當，並根據目前使用中的多位元組字碼頁來辨識多位元組字元序列。 **_wsplitpath**是寬字元版本的 **_splitpath**; **_wsplitpath**的引數是寬字元字串。 除此之外，這些函式的行為相同。

**安全性提示**這些函式可能會帶來緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

完整路徑的每個元件都會儲存在個別的緩衝區中;資訊清單常數 **_MAX_DRIVE**、 **_MAX_DIR**、 **_MAX_FNAME**和 **_MAX_EXT** （定義于 stdlib.h> 中。H）指定每個檔案元件的大小上限。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

每個緩衝區都必須與其對應的資訊清單常數一樣大，以避免潛在緩衝區滿溢。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路徑未包含元件（例如檔案名），則 **_splitpath**會將空字串指派給對應的緩衝區。

您可以針對不需要的*路徑*以外的任何參數，將**Null**傳遞給 **_splitpath** 。

如果*path*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_makepath](makepath-wmakepath.md) 的範例。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>

---
title: _splitpath、_wsplitpath
ms.date: 11/04/2016
apiname:
- _wsplitpath
- _splitpath
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
ms.openlocfilehash: d079bd17912c0711a4e1fbadadf12430520f2c96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465178"
---
# <a name="splitpath-wsplitpath"></a>_splitpath、_wsplitpath

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

*磁碟機*<br/>
磁碟機代號，後面接著冒號 (**:**)。 您可以傳遞**NULL**此參數，如果您不需要的磁碟機代號。

*dir*<br/>
目錄路徑，包括結尾斜線。 正斜線 ( **/** )，反斜線 ( **\\** )，或可以使用。 您可以傳遞**NULL**此參數，如果您不需要的目錄路徑。

*fname*<br/>
基底檔名 (無副檔名)。 您可以傳遞**NULL**此參數，如果您不需要檔案名稱。

*ext*<br/>
副檔名，包括前置句點 (**。**)。 您可以傳遞**NULL**此參數，如果您不需要檔名的副檔名。

## <a name="remarks"></a>備註

**_Splitpath**函式會分成四個元件中的路徑。 **_splitpath**自動多位元組字元字串引數處理為適當，辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。 **_wsplitpath**是寬字元版本的 **_splitpath**; 的引數 **_wsplitpath**是寬字元字串。 除此之外，這些函式的行為相同。

**安全性提示**這些函式可能會帶來緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。 這些函式已有更安全的版本可供使用，請參閱 [_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

完整路徑的每個元件都會儲存在個別的緩衝區;資訊清單常數 **_MAX_DRIVE**， **_MAX_DIR**， **_MAX_FNAME**，以及 **_MAX_EXT** （定義於 STDLIB。H） 指定每個檔案元件的大小上限。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

每個緩衝區都必須與其對應的資訊清單常數一樣大，以避免潛在緩衝區滿溢。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路徑未包含的元件 （例如，檔名）， **_splitpath**空字串指派給對應的緩衝區。

您可以傳遞**NULL**要 **_splitpath**以外的任何參數*路徑*，您不需要。

如果*路徑*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**EINVAL**。

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

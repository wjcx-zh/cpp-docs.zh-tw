---
title: _splitpath、_wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355604"
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

*路徑*<br/>
完整路徑。

*驅動*<br/>
驅動器號,後跟冒號 (**。** 如果不需要驅動器號,可以傳遞此參數的**NULL。**

*dir*<br/>
目錄路徑，包括結尾斜線。 可使用向前斜**/** 杠 ()、斜**\\**杠 () 或兩者。 如果不需要目錄路徑,可以傳遞此參數的**NULL。**

*fname*<br/>
基底檔名 (無副檔名)。 如果不需要檔名,可以傳遞此參數的**NULL。**

*內線*<br/>
檔案名副檔名,包括前導期 **(. 。** 如果不需要檔案名副檔名,可以傳遞此參數的**NULL。**

## <a name="remarks"></a>備註

**_splitpath**函數將路徑分解為四個元件。 **_splitpath**根據需要自動處理多位元位元串參數,根據當前使用的多位元組碼頁識別多位元組位元序列。 **_wsplitpath**是 **_splitpath**的寬字元版本;要 **_wsplitpath**的參數是寬字元字串。 除此之外，這些函式的行為相同。

**安全性提示**這些函式可能會帶來緩衝區滿溢問題所引發的威脅。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。 這些函數的更安全的版本可用;見[_splitpath_s,_wsplitpath_s。](splitpath-s-wsplitpath-s.md)

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

完整路徑的每個元件都存儲在單獨的緩衝區中;清單常量 **_MAX_DRIVE、_MAX_DIR、_MAX_FNAME**和 **_MAX_EXT(** 在 STDLIB 中定義)。 **_MAX_DRIVE** **_MAX_FNAME**H) 指定每個檔案元件的最大大小。 大於對應資訊清單常數的檔案元件會造成堆積損毀。

每個緩衝區都必須與其對應的資訊清單常數一樣大，以避免潛在緩衝區滿溢。

下表列出資訊清單常數的值。

|名稱|值|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

如果完整路徑不包含元件(例如檔名 **),_splitpath**將空字串分配給相應的緩衝區。

您可以將**NULL**傳遞給 **_splitpath**除*路徑*之外不需要的任何參數。

如果*路徑*為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續 **,errno**設定為**EINVAL,** 並且函數傳回**EINVAL**。

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

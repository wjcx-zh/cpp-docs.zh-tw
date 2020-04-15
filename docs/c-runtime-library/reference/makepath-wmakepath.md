---
title: _makepath、_wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341585"
---
# <a name="_makepath-_wmakepath"></a>_makepath、_wmakepath

從元件建立路徑名稱。 這些函式已有更安全的版本可用，請參閱 [_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)。

## <a name="syntax"></a>語法

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>參數

*路徑*<br/>
完整路徑緩衝區。

*驅動*<br/>
包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 **_makepath**如果缺少冒號,則會自動在複合路徑中插入冒號。 如果*驅動器*為**NULL**或指向空字串,則複合*路徑*字串中不會顯示驅動器號。

*dir*<br/>
包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 尾隨斜杠是可選的,在單個*dir*參數中可以使用前\\斜杠 (/) 或反斜杠 () 或兩者。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*為**NULL**或指向空字串,則複合路徑字串中未插入任何目錄*路徑*。

*fname*<br/>
包含基底檔案名稱，但不包含任何副檔名。 如果*fname*為**NULL**或指向空字串,則複合*路徑*字串中未插入任何檔案名。

*內線*<br/>
包含實際副檔名，可包含或不含前置句號 (.)。 如果期間未顯示在*分機*中 **,_makepath**自動插入期間。如果*分機*為**NULL**或指向空字串,則複合*路徑*字串中不會插入任何擴展。

## <a name="remarks"></a>備註

**_makepath**函數從單個元件創建復合路徑字串,將結果存儲在*路徑*中。 *路徑*可能包括驅動器號、目錄路徑、檔名和檔名副檔名。 **_wmakepath**是 **_makepath**的寬字元版本;要 **_wmakepath**的參數是寬字元字串。 **_wmakepath**和 **_makepath**行為相同。

**安全性提示**：使用以 Null 結束的字串。 為了避免緩衝區溢出,null 終止字串不得超過*路徑*緩衝區的大小。 **_makepath**不確保複合路徑字串的長度不超過 **_MAX_PATH**。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路徑*參數必須指向足夠大以容納完整路徑的空緩衝區。 複合*路徑*不能大於在 Stdlib.h 中定義的 **_MAX_PATH**常量。

如果路徑為**NULL,** 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 此外 **,errno**設定為**EINVAL**。 所有其他參數都允許**NULL**值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)<br/>

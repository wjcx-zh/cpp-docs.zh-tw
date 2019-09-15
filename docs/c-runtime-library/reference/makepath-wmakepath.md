---
title: _makepath、_wmakepath
ms.date: 11/04/2016
api_name:
- _makepath
- _wmakepath
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
ms.openlocfilehash: aafde0aeeebb7b773d3f96ca66ae65762dcdebdf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952932"
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

*path*<br/>
完整路徑緩衝區。

*drive*<br/>
包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 **_makepath**會在複合路徑中自動插入冒號（如果遺漏的話）。 如果*drive*是**Null**或指向空字串，複合*路徑*字串中就不會出現任何磁碟機號。

*dir*<br/>
包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 尾端斜線是選擇性的，而且可以在單一*dir*引數中使用正斜線（\\/）或反斜線（）或兩者。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*是**Null**或指向空字串，複合*路徑*字串中就不會插入任何目錄路徑。

*fname*<br/>
包含基底檔案名稱，但不包含任何副檔名。 如果*fname*為**Null**或指向空字串，複合*路徑*字串中就不會插入任何檔案名。

*ext*<br/>
包含實際副檔名，可包含或不含前置句號 (.)。 如果 **_makepath**未出現在*ext*中，則會自動插入句點。如果*ext*是**Null**或指向空字串，複合*路徑*字串中就不會插入任何副檔名。

## <a name="remarks"></a>備註

**_Makepath**函數會從個別元件建立複合路徑字串，並將結果儲存在*path*中。 *路徑*可能包含磁碟機號、目錄路徑、檔案名和副檔名。 **_wmakepath**是寬字元版本的 **_makepath**; **_wmakepath**的引數是寬字元字串。 相反地， **_wmakepath**和 **_makepath**的行為相同。

**安全性提示**：使用以 Null 結束的字串。 為避免緩衝區溢位，以 null 結束的字串不得超過*路徑*緩衝區的大小。 **_makepath**不會確保複合路徑字串的長度不會超過 **_MAX_PATH**。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*Path*引數必須指向夠大的空緩衝區，以容納完整的路徑。 複合*路徑*不能大於 **_MAX_PATH**常數，定義于 stdlib.h> 中。

如果 path 為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 此外， **errno**會設定為**EINVAL**。 所有其他參數都允許**Null**值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

---
title: _makepath、_wmakepath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21cfcfb8a1c82fb351b85b0fb169a94dd3c2c5d4
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105090"
---
# <a name="makepath-wmakepath"></a>_makepath、_wmakepath

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

*磁碟機*<br/>
包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 **_makepath**冒號自動插入複合路徑中遺失。 如果*磁碟機*是**NULL**或指向空字串，不要的磁碟機代號會出現在複合*路徑*字串。

*dir*<br/>
包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 結尾的斜線是選擇性的並正斜線 （/） 或反斜線 (\\)，或是兩者都可能會用於在單一*dir*引數。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*是**NULL**或指向空字串，沒有目錄路徑會插入複合*路徑*字串。

*fname*<br/>
包含基底檔案名稱，但不包含任何副檔名。 如果*fname*是**NULL**或指向空字串，任何檔名會插入複合*路徑*字串。

*ext*<br/>
包含實際副檔名，可包含或不含前置句號 (.)。 **_makepath**自動插入句號，如果它不會出現在*ext*。如果*ext*是**NULL**或指向空字串，不含副檔名會插入複合*路徑*字串。

## <a name="remarks"></a>備註

**_Makepath**函式會從 個別元件，儲存在結果中建立複合路徑字串*路徑*。 *路徑*可能包含磁碟機代號、 目錄路徑、 檔名和副檔名。 **_wmakepath**是寬字元版本的 **_makepath**; 的引數 **_wmakepath**是寬字元字串。 **_wmakepath**並 **_makepath**行為相同。

**安全性提示**：使用以 Null 結束的字串。 若要避免緩衝區溢位，以 null 結束的字串不得超過的大小*路徑*緩衝區。 **_makepath**無法確保複合路徑字串的長度不超過 **_MAX_PATH**。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路徑*引數必須指向空的緩衝區不夠大，無法容納完整路徑。 複合*路徑*必須是不能大於 **_MAX_PATH**在 Stdlib.h 中定義的常數。

如果路徑**NULL**，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 颾魤 ㄛ **errno**設為**EINVAL**。 **NULL**允許所有其他參數的值。

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

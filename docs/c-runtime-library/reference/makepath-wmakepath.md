---
title: _makepath、_wmakepath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6ad1331021331e9c9ddc1d1344aae8ed164ce2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*路徑*完整路徑緩衝區。

*磁碟機*包含字母 （A、 B 和等等） 對應至所需的磁碟機和選擇性結尾的冒號。 **_makepath**冒號自動插入複合路徑中遺漏時。 如果*磁碟機*是**NULL**或指向空字串時，沒有磁碟機代號會出現在複合*路徑*字串。

*dir*包含路徑的目錄，不包括磁碟機指示項或實際的檔案名稱。 句尾斜線是選用的並正斜線 （/） 或反斜線 (\\) 或兩者都可能會使用單一*dir*引數。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果*dir*是**NULL**指向空字串，沒有目錄路徑在複合插入或*路徑*字串。

*fname*包含的基底檔案名稱沒有任何檔案名稱的副檔名。 如果*fname*是**NULL**或空字串，任何檔名指向插入複合*路徑*字串。

*ext*包含實際的檔案名稱副檔名，或不含前置句號 （.）。 **_makepath**自動插入期間，如果它不會顯示在*ext*。如果*ext*是**NULL**或空字串，沒有副檔名的點插入複合*路徑*字串。

## <a name="remarks"></a>備註

**_Makepath**函式會建立複合路徑字串儲存在該結果的個別元件來自*路徑*。 *路徑*可能包括磁碟機代號、 目錄路徑、 檔名和副檔名。 **_wmakepath**是寬字元版本的 **_makepath**; 的引數 **_wmakepath**是寬字元字串。 **_wmakepath**和 **_makepath**除此之外的行為相同。

**安全性提示**：使用以 Null 結束的字串。 若要避免緩衝區滿溢，null 結束的字串不能超過大小*路徑*緩衝區。 **_makepath**不會保證複合路徑字串的長度不超過 **_MAX_PATH**。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*路徑*引數必須指向空的緩衝區不夠大，無法保存完整路徑。 複合*路徑*必須不能大於 **_MAX_PATH** Stdlib.h 中定義的常數。

如果路徑是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 此外， **errno**設**EINVAL**。 **NULL**允許所有其他參數值。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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

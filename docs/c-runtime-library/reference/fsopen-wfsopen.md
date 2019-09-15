---
title: _fsopen、_wfsopen
ms.date: 11/04/2016
api_name:
- _wfsopen
- _fsopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: 1ffc3aa5801ff2ed63ecf815f3351e4d7a8cf459
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956473"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen、_wfsopen

以檔案共用開啟資料流。

## <a name="syntax"></a>語法

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>參數

*filename*<br/>
要開啟的檔案之名稱。

*mode*<br/>
允許的存取類型。

*shflag*<br/>
允許的共用類型。

## <a name="return-value"></a>傳回值

這些函式中每一個都會傳回資料流的指標。 null 指標值表示錯誤。 如果*filename*或*mode*是**Null**或空字串，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會傳回**Null** , 並將**Errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Fsopen**函式會將*filename*指定的檔案開啟為數據流，並準備檔案以進行後續的共用讀取或寫入，如 mode 和*shflag*引數所定義。 **_wfsopen**是寬字元版本的 **_fsopen**; **_wfsopen**的*檔案名*和*模式*引數是寬字元字串。 相反地， **_wfsopen**和 **_fsopen**的行為相同。

字元字串*模式*會指定對檔案要求的存取類型，如下表所示。

|詞彙|定義|
|----------|----------------|
|**"r"**|開啟以讀取。 如果檔案不存在或找不到， **_fsopen**呼叫將會失敗。|
|**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a"**|開啟以寫入該檔案結尾 (附加)；如果該檔案不存在，便會先建立檔案。|
|**"r+"**|開啟以進行讀取和寫入。 (檔案必須存在)。|
|**"w+"**|開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a+"**|開啟以寫入和附加；如果該檔案不存在，便會先建立檔案。|

請小心使用 **"w"** 和 **"w +"** 類型, 因為它們可以摧毀現有的檔案。

以 **"a"** 或 **"a +"** 存取類型開啟檔案時，所有寫入作業都會在檔案結尾進行。 您可以使用[fseek](fseek-fseeki64.md) [或倒轉](rewind.md)來重新置放檔案指標，但是在執行任何寫入作業之前，一律會移回至檔案結尾。因此，無法覆寫現有資料。 當指定了 **"r +"** 、 **"w +"** 或 **"a +"** 存取類型時，會允許讀取和寫入（此檔案稱為「已開啟」進行更新）。 不過，在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md)或 [rewind](rewind.md) 作業。 如有需要, 可以為[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)作業指定目前的位置。 除了上述的值之外，您還可以在*模式*中包含下列其中一個字元，以指定新行的轉譯模式和檔案管理。

|詞彙|定義|
|----------|----------------|
|**t**|以文字 (已轉譯) 模式開啟檔案 在此模式中，會將換行字元（CR-LF）組合轉譯為輸入上的單行換行（LF），而分行符號則會在輸出時轉譯成 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在為了讀取或讀取/寫入而開啟的檔案中， **_fsopen**會檢查檔案結尾是否有 CTRL + Z，並盡可能加以移除。 這是因為使用[fseek](fseek-fseeki64.md)和[FTELL](ftell-ftelli64.md)在以 CTRL + Z 結尾的檔案內移動，可能會導致[fseek](fseek-fseeki64.md)在檔案結尾附近的行為不正確。|
|**b**|在二進位 (未轉譯) 模式中開啟檔案；會隱藏上述轉譯。|
|**S**|指定針對但不限於磁碟的循序存取進行快取最佳化。|
|**R**|指定針對但不限於磁碟的隨機存取進行快取最佳化。|
|**T**|指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。|
|**D**|指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。|

如果 *mode* 中未指定 **t** 或 **b**，則轉譯模式由預設模式變數 **_fmode** 所定義。 如果**t**或**b**前面加上引數, 則函式會失敗並傳回**Null**。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

引數*shflag*是常數運算式，其中包含定義于 Share. h 中的下列其中一個資訊清單常數。

|詞彙|定義|
|----------|----------------|
|**_SH_COMPAT**|設定 16 位元應用程式的相容性模式。|
|**_SH_DENYNO**|允許讀取及寫入權限。|
|**_SH_DENYRD**|拒絕對該檔案的讀取存取。|
|**_SH_DENYRW**|拒絕對該檔案的讀取和寫入存取。|
|**_SH_DENYWR**|拒絕對該檔案的寫入存取。|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>需求

|函數|必要的標頭|選擇性標頭|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> 適用于*shflag*參數的資訊清單常數。|
|**_wfsopen**|\<stdio.h> 或 \<wchar.h>|\<share.h><br /><br /> 適用于*shflag*參數的資訊清單常數。|

## <a name="example"></a>範例

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>

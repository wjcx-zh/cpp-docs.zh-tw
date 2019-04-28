---
title: _fsopen、_wfsopen
ms.date: 11/04/2016
apiname:
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 197a4f690a6626edbfec27ea4abef1999b6cedaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287692"
---
# <a name="fsopen-wfsopen"></a>_fsopen、_wfsopen

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

這些函式中每一個都會傳回資料流的指標。 null 指標值表示錯誤。 如果*檔名*或是*模式*會**NULL**或空字串，這些函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，則這些函式會傳回**NULL**並設定**errno**來**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Fsopen**函式會開啟所指定的檔案*filename*做為資料流並準備檔案以供後續的共用的讀取或寫入，所定義的模式和*shflag*引數。 **_wfsopen**是寬字元版本的 **_fsopen**; *filename*並*模式*引數 **_wfsopen**是寬字元字串。 **_wfsopen**並 **_fsopen**行為相同。

字元字串*模式*指定要求檔案的存取類型下, 表所示。

|詞彙|定義|
|----------|----------------|
|**"r"**|開啟以讀取。 如果檔案不存在或無法找到 **_fsopen**呼叫就會失敗。|
|**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a"**|開啟以寫入該檔案結尾 (附加)；如果該檔案不存在，便會先建立檔案。|
|**"r+"**|開啟以進行讀取和寫入。 (檔案必須存在)。|
|**"w+"**|開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a+"**|開啟以寫入和附加；如果該檔案不存在，便會先建立檔案。|

使用 **"w"** 並 **"w +"** 類型使用時請小心，因為它們可以終結現有的檔案。

與開啟檔案時 **"a"** 或是 **"a +"** 存取類型，所有寫入作業都會在檔案結尾。 檔案指標可以使用定位[fseek](fseek-fseeki64.md)或是[倒轉](rewind.md)，但它會永遠移回至檔案結尾之前的作業會執行任何寫入。因此，無法覆寫現有資料。 當 **"r +"**， **"w +"**，或 **"a +"** 指定存取類型，允許讀取和寫入 （檔案要開啟以供更新）。 不過，在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md)或 [rewind](rewind.md) 作業。 可以指定目前的位置，如[fsetpos](fsetpos.md)或是[fseek](fseek-fseeki64.md)作業，如有需要。 除了上述的值，其中一個下列的字元可以包含在*模式*來指定新行和檔案管理的轉譯模式。

|詞彙|定義|
|----------|----------------|
|**t**|以文字 (已轉譯) 模式開啟檔案 在此模式中，歸位換摘要 (CR-LF) 組合在輸入上，會轉譯成單行換 (LF)，和 LF 字元會轉譯為 CR-LF 組合，在輸出上。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在檔案開啟供讀取或讀取/寫入， **_fsopen**會檢查是否有 CTRL + Z 結尾的檔案，並盡可能加以移除。 這是因為使用[fseek](fseek-fseeki64.md)並[ftell](ftell-ftelli64.md) CTRL + Z 結束可能會導致檔案內移動[fseek](fseek-fseeki64.md)檔案結尾附近產生不當行為。|
|**b**|在二進位 (未轉譯) 模式中開啟檔案；會隱藏上述轉譯。|
|**S**|指定針對但不限於磁碟的循序存取進行快取最佳化。|
|**R**|指定針對但不限於磁碟的隨機存取進行快取最佳化。|
|**T**|指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。|
|**D**|指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。|

如果 *mode* 中未指定 **t** 或 **b**，則轉譯模式由預設模式變數 **_fmode** 所定義。 如果**t**或是**b**前面加上引數，函式會失敗並傳回**NULL**。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

引數*shflag*是常數運算式，其中包含下列資訊清單常數，定義在 Share.h 中的其中一個。

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

|功能|必要的標頭|選擇性標頭|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> 為資訊清單常數*shflag*參數。|
|**_wfsopen**|\<stdio.h> 或 \<wchar.h>|\<share.h><br /><br /> 為資訊清單常數*shflag*參數。|

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

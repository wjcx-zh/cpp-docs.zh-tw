---
title: _fsopen、_wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345692"
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

*檔案名稱*<br/>
要開啟的檔案之名稱。

*模式*<br/>
允許的存取類型。

*什弗拉格*<br/>
允許的共用類型。

## <a name="return-value"></a>傳回值

這些函式中每一個都會傳回資料流的指標。 null 指標值表示錯誤。 如果*檔案名稱*或*模式*為**NULL**或空字串,這些函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將傳回**NULL**並將**errno**設定為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_fsopen**函數將*檔名*指定的文件作為流打開,並為檔案準備供後續共用讀取或寫入(由模式定義)和 *"鞭打*參數"。 **_wfsopen**是 **_fsopen**的寬字元版本;要 **_wfsopen***的檔案名稱*和*模式*參數是寬字元字串。 **_wfsopen**和 **_fsopen**行為相同。

字串*模式*指定為檔案請求的存取類型,如下表所示。

|詞彙|定義|
|----------|----------------|
|**"r"**|開啟以讀取。 如果檔案不存在或找不到,**則_fsopen**呼叫失敗。|
|**"w"**|開啟空白檔案以寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a"**|開啟以寫入該檔案結尾 (附加)；如果該檔案不存在，便會先建立檔案。|
|**"r+"**|開啟以進行讀取和寫入。 (檔案必須存在)。|
|**"w+"**|開啟空白檔案以進行讀取和寫入。 如果指定的檔案已存在，其內容將被終結。|
|**"a+"**|開啟以寫入和附加；如果該檔案不存在，便會先建立檔案。|

小心使用 **"w"** 和 **"w+"** 類型,因為它們可以銷毀現有檔。

當使用 **"a"或"a+"** 存取 **"a+"** 類型打開檔時,所有寫入操作都發生在檔的末尾。 可以使用[fseek](fseek-fseeki64.md)或[後退](rewind.md)重新定位檔指標,但在執行任何寫入操作之前,該檔指標始終被移回檔末尾。因此,無法覆蓋現有數據。 指定 **"r+"、"w+"** 或 **"w+"****"a+"** 存取類型時,允許讀取和寫入(該檔表示打開以進行更新)。 不過，在讀取和寫入之間切換時，必須有中間的 [fsetpos](fsetpos.md)、[fseek](fseek-fseeki64.md)或 [rewind](rewind.md) 作業。 如果需要,可以為[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作指定當前位置。 除了上述值之外,還可以將以下字元之一包含在*模式下*,以指定新行的轉換模式和檔管理。

|詞彙|定義|
|----------|----------------|
|**t**|以文字 (已轉譯) 模式開啟檔案 在此模式下,車廂回饋送 (CR-LF) 組合在輸入時轉換為單行饋送 (LF),在輸出時將 LF 字元轉換為 CR-LF 組合。 此外，Ctrl+Z 會在輸入中解譯成檔案結尾字元。 在打開用於讀取或讀取/寫入的檔中 **,_fsopen**檢查檔末尾的 CTRL_Z 並盡可能將其刪除。 這樣做是因為使用[fseek](fseek-fseeki64.md)和[ftell](ftell-ftelli64.md)在以 CTRL_Z 結尾的檔內移動可能會導致[fseek](fseek-fseeki64.md)在檔末尾附近行為不當。|
|**B**|在二進位 (未轉譯) 模式中開啟檔案；會隱藏上述轉譯。|
|**S**|指定針對但不限於磁碟的循序存取進行快取最佳化。|
|**R**|指定針對但不限於磁碟的隨機存取進行快取最佳化。|
|**T**|指定檔案做為暫存檔。 可能的話，不將其清除至磁碟。|
|**D**|指定檔案做為暫存檔。 當最後一個檔案指標關閉時，將其刪除。|

如果 *mode* 中未指定 **t** 或 **b**，則轉譯模式由預設模式變數 **_fmode** 所定義。 如果**t**或**b**預置到參數,則函數會失敗並傳回**NULL**。 如需文字和二進位模式的討論，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

參數*shflag*是一個常量運算式,由以下清單常量之一組成,在 Share.h 中定義。

|詞彙|定義|
|----------|----------------|
|**_SH_COMPAT**|設定 16 位元應用程式的相容性模式。|
|**_SH_DENYNO**|允許讀取和寫入存取。|
|**_SH_DENYRD**|拒絕對該檔案的讀取存取。|
|**_SH_DENYRW**|拒絕對該檔案的讀取和寫入存取。|
|**_SH_DENYWR**|拒絕對該檔案的寫入存取。|

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> 對於*shflag*參數的清單常量。|
|**_wfsopen**|\<stdio.h> 或 \<wchar.h>|\<share.h><br /><br /> 對於*shflag*參數的清單常量。|

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
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>

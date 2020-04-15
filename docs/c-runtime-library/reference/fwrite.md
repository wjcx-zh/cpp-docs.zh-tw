---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345399"
---
# <a name="fwrite"></a>fwrite

將資料寫入資料流。

## <a name="syntax"></a>語法

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
要寫入之資料的指標。

*大小*<br/>
項目大小 (位元組)。

*count*<br/>
要寫入之項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fwrite**傳回實際寫入的完整項目,如果發生錯誤,該項可能小於*計數*。 此外，若發生錯誤，也無法判斷檔案位置指標。 如果*流*或*緩衝區*是空指標,或者如果在 Unicode 模式下指定了奇數的位元組,則函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回0。

## <a name="remarks"></a>備註

**fwrite**函數寫入*以計算*從*緩衝區*到輸出*流*的項,每個*項的大小*長度。 與*流*關聯的檔指標(如果有)將遞增為實際寫入的位元組數。 如果在文字模式下打開*流*,則每個換行符將替換為回車換行對。 這種取代不會對傳回值產生影響。

在 Unicode 轉換模式下打開*流*時(例如,如果通過調用**fopen**並使用包含**ccs=UNICODE**ccs_UNICODE、ccs_UTF-16LE 或**ccs_UTF-8**的模式**ccs=UTF-16LE**參數)打開*流*,或者通過使用 **_setmode**和包含 **_O_WTEXT、_O_U16TEXT**或 **_O_U8TEXT***緩衝區*的模式參數將 **_O_U16TEXT**模式更改為包含 UTF-16 的**wchar_t**數位組的指標。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

因為此函示會鎖定呼叫執行緒，這是安全執行緒。 有關非鎖定版本,請參閱 **_fwrite_nolock**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fread](fread.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>

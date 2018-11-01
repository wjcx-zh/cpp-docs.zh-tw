---
title: fwrite
ms.date: 11/04/2016
apiname:
- fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: b4d6b9ce4fb66ee545f52946e28e4984d9e4f924
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506739"
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

*buffer*<br/>
要寫入之資料的指標。

*size*<br/>
項目大小 (位元組)。

*count*<br/>
要寫入之項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fwrite**傳回的完整實際寫入的項目，這可能會小於*計數*發生錯誤。 此外，若發生錯誤，也無法判斷檔案位置指標。 如果有任一*資料流*或是*緩衝區*為 null 指標，或如果奇數數目的可寫入的位元組會指定在 Unicode 模式中，函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**且會傳回 0。

## <a name="remarks"></a>備註

**Fwrite**函式會寫入最多*計數*項目 的*大小*長度，從*緩衝區*輸出*資料流*. 與相關聯的檔案指標*資料流*（如果有的話） 會遞增的實際寫入的位元組數目。 如果*資料流*開啟在文字模式中，每個換行字元會取代為歸位/換行字元組。 這種取代不會對傳回值產生影響。

當*資料流*在 Unicode 轉譯模式中開啟 — 比方說，如果*串流*開啟藉由呼叫**fopen**和使用模式參數，其包含**ccs= UNICODE**， **ccs =-16LE**，或**ccs = utf-8**，或如果模式變更為 Unicode 轉譯模式使用 **_setmode**和模式包含的參數 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**—*緩衝區*會解譯為變數的指標，陣列**wchar_t**包含 utf-16 資料。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

因為此函示會鎖定呼叫執行緒，這是安全執行緒。 如需非鎖定版本，請參閱 < **_fwrite_nolock**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fread](fread.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>

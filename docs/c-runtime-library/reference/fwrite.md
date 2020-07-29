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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b604819391629d057850c17466807e7c329c472d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198589"
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

*size*<br/>
項目大小 (位元組)。

*計數*<br/>
要寫入之項目的最大數量。

*資料流程*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fwrite**會傳回實際寫入的完整專案數，如果發生錯誤，可能會小於*計數*。 此外，若發生錯誤，也無法判斷檔案位置指標。 如果*資料流程*或*緩衝區*是 null 指標，或者如果要寫入的奇數位節數目是以 Unicode 模式指定，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回0。

## <a name="remarks"></a>備註

**Fwrite**函式*會將每個專案的**大小*上限，從*緩衝區*寫入輸出*資料流程*。 與*資料流程*相關聯的檔案指標（如果有的話）會以實際寫入的位元組數遞增。 如果在文字模式中開啟*資料流程*，則會將每個換行字元換行一組。 這種取代不會對傳回值產生影響。

以 Unicode 轉譯模式開啟*資料流程*時，例如如果已藉由呼叫**fopen**並使用包含**ccs = Unicode**、 **ccs = utf-utf-16le**或**ccs = utf-8**的模式參數來開啟*資料流程*，或如果模式已使用 **_Setmode**和包含 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**的模式參數變更為 Unicode 轉譯模式，則會將*緩衝區*解讀為 **`wchar_t`** 包含 utf-16 資料之陣列的指標。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。

因為此函示會鎖定呼叫執行緒，這是安全執行緒。 如需非鎖定版本，請參閱 **_fwrite_nolock**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

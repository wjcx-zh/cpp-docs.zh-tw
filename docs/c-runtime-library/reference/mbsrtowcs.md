---
title: mbsrtowcs
ms.date: 11/04/2016
api_name:
- mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: de7b25ea8a520dfe2c9cb26ec8989624b670dcb9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952042"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

將目前地區設定的多位元組字元字串轉換成對應的寬字元字串，並提供在多位元組字元中間重新啟動的功能。 這個函式已有更安全的版本可用，請參閱 [mbsrtowcs_s](mbsrtowcs-s.md)。

## <a name="syntax"></a>語法

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*wcstr*<br/>
用來儲存所產生之已轉換寬字元字串的位址。

*mbstr*<br/>
要轉換之多位元組字元字串位置的間接指標。

*計數*<br/>
要轉換並儲存在*wcstr*中的最大字元數（不是位元組）。

*mbstate*<br/>
**Mbstate_t**轉換狀態物件的指標。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是安全線程，因此建議您一律傳遞自己的*mbstate*參數。

## <a name="return-value"></a>傳回值

傳回成功轉換的字元數，但不包含結束的 null 字元 (如果有的話)。 如果發生錯誤，則傳回（size_t）（-1），並將**errno**設定為 EILSEQ。

## <a name="remarks"></a>備註

**Mbsrtowcs**函式會使用*mbstate*中包含的轉換狀態，將*mbstr*間接指向的多位元組字元字串轉換為*wcstr*所指向之緩衝區中儲存的寬字元。 每個字元的轉換會繼續進行，直到遇到終止的 null 多位元組字元、遇到未對應到目前地區設定中有效字元的多位元組序列，或直到*計數*字元已轉換. 如果**mbsrtowcs**在之前或發生*計數*時遇到多位元組 null 字元（' \ 0 '），則會將它轉換成16位終止的 null 字元，並停止。

因此，只有在**mbsrtowcs**在轉換期間遇到多位元組的 null 字元時， *wcstr*的寬字元字串才會以 null 結束。 如果*mbstr*和*wcstr*所指向的序列重迭，則**mbsrtowcs**的行為會是未定義的。 **mbsrtowcs**會受到目前地區設定的 LC_TYPE 類別目錄所影響。

**Mbsrtowcs**函式與[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用**mbsrtowcs**的後續呼叫，而不是**mbstowcs**，則應用程式應該使用**mbsrlen**而不是**mbslen**。

如果*wcstr*不是 null 指標，則會在轉換因為到達結束的 null 字元而停止時，將 null 指標指派給*mbstr*所指向的指標物件。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*wcstr*引數為 null 指標，則會忽略*count*引數，而**mbsrtowcs**會傳回目的字串所需的寬字元大小。 如果*mbstate*是 null 指標，此函式會使用非安全線程的靜態內部**mbstate_t**轉換狀態物件。 如果字元順序*mbstr*沒有對應的多位元組字元標記法，則會傳回-1，並將**Errno**設定為**EILSEQ**。

如果*mbstr* isa null 指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回-1。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

只要此函式正在執行，而且*mbstate*引數不是 null 指標， **mbsrtowcs**函式就是多執行緒安全，前提是目前線程中的任何函式都不會呼叫**setlocale** 。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>

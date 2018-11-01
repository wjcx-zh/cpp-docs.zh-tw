---
title: mbsrtowcs
ms.date: 11/04/2016
apiname:
- mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 2bc0c8c9e2d871b6d1748c42dc02c627244dbf69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597141"
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

*count*<br/>
若要轉換並儲存在字元 （而不是個位元組） 的數目上限*wcstr*。

*mbstate*<br/>
指標**mbstate_t**轉換狀態物件。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 因為內部**mbstate_t**物件不是執行緒安全，我們建議您一律傳遞自己*mbstate*參數。

## <a name="return-value"></a>傳回值

傳回成功轉換的字元數，但不包含結束的 null 字元 (如果有的話)。 傳回 (size_t)(-1) 如果錯誤發生，並設定**errno**設為 EILSEQ。

## <a name="remarks"></a>備註

**Mbsrtowcs**函式將間接所指向的多位元組字元字串轉換*mbstr*，到儲存在緩衝區所指向的寬字元*wcstr*、 藉由使用包含的轉換狀態*mbstate*。 轉換會繼續為每個字元之前遇到其中一個結束的 null 多位元組字元時，遇到沒有對應至目前的地區設定中的有效字元的多位元組序列時，或直到*計數*已轉換的字元。 如果**mbsrtowcs**之前或期間遇到 null 多位元組字元 ('\0')*計數*發生時，會將其轉換成 16 位元結束的 null 字元並停止。

因此，在寬字元字串*wcstr*是以 null 終止才**mbsrtowcs**轉換期間遇到 null 多位元組字元。 如果指向的序列所*mbstr*並*wcstr*重疊，就會有的行為**mbsrtowcs**是未定義。 **mbsrtowcs**會受到目前地區設定之 LC_TYPE 分類。

**Mbsrtowcs**函式與不同[mbstowcs、 _mbstowcs_l](mbstowcs-mbstowcs-l.md)重新。 轉換狀態會儲存在*mbstate*的後續呼叫相同或其他可重新啟動的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，應用程式應該使用**mbsrlen**而不是**mbslen**，如果後續呼叫**mbsrtowcs**改用**mbstowcs**.

如果*wcstr*不是 null 指標，指向的指標物件*mbstr*會指派 null 指標，如果轉換已停止，因為已達結束的 null 字元。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*wcstr*引數是 null 指標，*計數*會忽略引數並**mbsrtowcs**傳回目的地字串的寬字元的所需的大小。 如果*mbstate*為 null 指標，此函數會使用非安全執行緒靜態內部**mbstate_t**轉換狀態物件。 如果字元序列*mbstr*沒有對應的多位元組字元表示法，則傳回-1 並**errno**設定為**EILSEQ**。

如果*mbstr*為 null 指標，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**並傳回-1。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Mbsrtowcs**函式是多執行緒的安全，只要在目前的執行緒中的任何函式會呼叫**setlocale**只要這個函式執行和*mbstate*引數不是 null 指標。

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

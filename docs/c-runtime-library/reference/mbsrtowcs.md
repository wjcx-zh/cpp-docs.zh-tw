---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338889"
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

*wc斯特*<br/>
用來儲存所產生之已轉換寬字元字串的位址。

*姆布斯特*<br/>
要轉換之多位元組字元字串位置的間接指標。

*count*<br/>
要在*wcstr*中轉換和存儲的最大字元數(而不是位元組數)。

*mbstate*<br/>
指向**mbstate_t**轉換狀態物件的指標。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是線程安全的,因此我們建議您始終傳遞自己的*mbstate*參數。

## <a name="return-value"></a>傳回值

傳回成功轉換的字元數，但不包含結束的 null 字元 (如果有的話)。 如果發生錯誤,則返回 (size_t)(-1),並將**errno**設置到 EILSEQ。

## <a name="remarks"></a>備註

**mbsrtowcs**函數通過使用*mbstate*中包含的轉換狀態,將*mbstr*間接指向的多位元組字元字串轉換為存儲在*wcstr*指向的緩衝區中的寬字元。 每個字元的轉換將繼續,直到遇到終止 null 多位元組位元元、遇到與當前區域設置中的有效字元不對應的多位元組序列,或直到*計數*字元已轉換。 如果**mbsrtowcs**在*計數*發生之前或發生計數時遇到多位元組空字元 ("\0"),它將轉換為 16 位元終止空字元並停止。

因此,僅當**mbsrtowcs**在轉換期間遇到多位元組空字元時 *,wcstr*處的寬字元字串才為null終止。 如果*mbstr*和*wcstr*指向的序列重疊,則**mbsrtowcs**的行為未定義。 **mbsrtowcs**受當前區域設置LC_TYPE類別的影響。

**mbsrtowcs**函數不同於[mbstowcs,_mbstowcs_l](mbstowcs-mbstowcs-l.md)它的可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如,如果使用對**mbsrtowc 的**後續呼叫而不是**mbstowcs,** 則應用程式應使用**mbsrlen**而不是**mbslen。**

如果*wcstr*不是空指標,則如果由於達到終止空字元而停止轉換,則*mbstr*指向的指針對象將分配一個空指標。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*wcstr*參數是空指標,則忽略*count*參數 **,mbsrtowcs**返回目標字串所需的寬字元大小。 如果*mbstate*是空指標,則函數使用非線程安全靜態**mbstate_t**轉換狀態物件。 如果字元序列*mbstr*沒有相應的多位元組字元表示形式,則傳回 -1 並將**errno**設定為**EILSEQ**。

如果*mbstr*是空指標,則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回 -1。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

只要此函式正在執行並且*mbstate*參數不是空指標 **,mbsrtowcs**函數是多線程安全的,只要當前線程呼叫中沒有函數**設定局部性**。

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

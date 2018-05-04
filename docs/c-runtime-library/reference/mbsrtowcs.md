---
title: mbsrtowcs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccb5bda16238888905678ffb3b6de01b93555ad0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
要轉換並儲存在字元 （而不是個位元組） 的數目上限*wcstr*。

*mbstate*<br/>
指標**mbstate_t**轉換狀態物件。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 因為內部**mbstate_t**物件不是執行緒安全，我們建議您一律傳遞您自己*mbstate*參數。

## <a name="return-value"></a>傳回值

傳回成功轉換的字元數，但不包含結束的 null 字元 (如果有的話)。 傳回 (如果錯誤發生，且設定 size_t)(-1) **errno**設為 EILSEQ。

## <a name="remarks"></a>備註

**Mbsrtowcs**函式所間接指向的多位元組字元字串，轉換為*mbstr*，儲存在緩衝區所指向的寬字元到*wcstr*、 藉由中所包含的轉換狀態*mbstate*。 轉換會繼續為每個字元之前遇到任一個結束的 null 多位元組字元時，遇到未對應到目前的地區設定的有效字元的多位元組序列時，或直到*計數*已轉換的字元。 如果**mbsrtowcs**之前或期間遇到 null 多位元組字元 ('\0')*計數*發生時，會將它轉換成 16 位元結束的 null 字元而停止。

因此，在寬字元字串*wcstr*是以 null 終止才**mbsrtowcs**轉換期間遇到 null 多位元組字元。 如果指向的序列*mbstr*和*wcstr*重疊，行為**mbsrtowcs**是未定義。 **mbsrtowcs**會受到目前地區設定之 LC_TYPE 分類。

**Mbsrtowcs**函式不同於[mbstowcs、 _mbstowcs_l](mbstowcs-mbstowcs-l.md)重新。 轉換狀態會儲存在*mbstate*的相同或其他可重新啟動的函式的後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，應用程式應該使用**mbsrlen**而不是**mbslen**，如果的後續呼叫**mbsrtowcs**而非**mbstowcs**.

如果*wcstr*不是 null 指標，指向的指標物件*mbstr*會指派給 null 指標，如果由於達到結束的 null 字元而停止轉換。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*wcstr*引數是 null 指標，*計數*會忽略引數和**mbsrtowcs**傳回所需的大小的寬字元目的字串。 如果*mbstate*為 null 指標，此函數會使用非安全執行緒的靜態內部**mbstate_t**轉換狀態物件。 如果字元序列*mbstr*沒有對應的多位元組字元表示法，則傳回-1 和**errno**設**EILSEQ**。

如果*mbstr*為 null 指標，無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回-1。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Mbsrtowcs**函式是多執行緒安全，只要在目前執行緒中的任何函式呼叫**setlocale** ，只要這個函式執行和*mbstate*引數不是 null 指標。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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

---
title: mbsrtowcs_s
ms.date: 11/04/2016
api_name:
- mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: d79cceaf923c1da126a1d133a8d2eb8752883457
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952092"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

將目前的地區設定的多位元組字元字串，轉換為寬字元字串的表示。 這是 [mbsrtowcs](mbsrtowcs.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>參數

*pReturnValue*<br/>
已轉換的字元數。

*wcstr*<br/>
緩衝區位址，要儲存產生的已轉換寬字元字串。

*sizeInWords*<br/>
*Wcstr*的大小（以單字（寬字元）為單位）。

*mbstr*<br/>
要轉換的多位元組字元字串位置的間接指標。

*計數*<br/>
要儲存在*wcstr*緩衝區中的寬字元數目上限，不包括終止的 Null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
**Mbstate_t**轉換狀態物件的指標。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是安全線程，因此建議您一律傳遞自己的*mbstate*參數。

## <a name="return-value"></a>傳回值

如果轉換成功為零，若失敗則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*wcstr*是 null 指標，而*sizeInWords* > 0|**EINVAL**|
|*mbstr*是 null 指標|**EINVAL**|
|*Mbstr*間接指向的字串包含對目前地區設定不正確多位元組序列。|**EILSEQ**|
|目的緩衝區太小，無法包含已轉換的字串（除非*count*為 **_TRUNCATE**; 如需詳細資訊，請參閱備註）|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼並設定**errno** ，如下表所示。

## <a name="remarks"></a>備註

**Mbsrtowcs_s**函式會使用*mbstate*中包含的轉換狀態，將*mbstr*間接指向的多位元組字元字串轉換成*wcstr*所指向之緩衝區中儲存的寬字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到多位元組的 null 字元

- 遇到無效的多位元組字元

- 儲存在*wcstr*緩衝區中的寬字元數等於*count*。

除非*wcstr*是 null 指標，否則目的地字串*wcstr*一律會以 null 結束，即使發生錯誤也一樣。

如果*count*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)， **mbsrtowcs_s**會盡可能將字串轉換成符合目的緩衝區，同時仍留出空間給 null 結束字元。

如果**mbsrtowcs_s**成功轉換來源字串，則會將已轉換字串的寬字元大小和 null 結束字元放入 *&#42;pReturnValue*，前提是*pReturnValue*不是 null 指標。 即使*wcstr*引數是 null 指標，而且可讓您決定所需的緩衝區大小，也會發生這種情況。 請注意，如果*wcstr*是 null 指標，則會忽略*count* 。

如果*wcstr*不是 null 指標，則會在轉換因為到達結束的 null 字元而停止時，將 null 指標指派給*mbstr*所指向的指標物件。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*mbstate*為 null 指標，則會使用程式庫內部**mbstate_t**轉換狀態靜態物件。 由於這個內部靜態物件不是安全線程，因此建議您傳遞自己的*mbstate*值。

如果**mbsrtowcs_s**遇到目前地區設定中不正確多位元組字元，它會將-1 放在 *&#42;pReturnValue*中，將目的地緩衝區*wcstr*設定為空字串，將**errno**設定為**EILSEQ**，然後傳回**EILSEQ**。

如果*mbstr*和*wcstr*所指向的序列重迭，則**mbsrtowcs_s**的行為會是未定義的。 **mbsrtowcs_s**會受到目前地區設定的 LC_TYPE 類別目錄所影響。

> [!IMPORTANT]
> 請確定*wcstr*和*mbstr*不會重迭，而且該*計數*會正確反映要轉換的多位元組字元數。

**Mbsrtowcs_s**函式與[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用**mbsrtowcs_s**的後續呼叫，而不是**mbstowcs_s**，則應用程式應該使用**mbsrlen**而不是**mbslen**。

C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以使用較新且安全的對應函式，來自動取代不安全的舊函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

如果目前線程中沒有函數正在執行，而且*mbstate*引數不是 null 指標，則**mbsrtowcs_s**函數會是多執行緒安全。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s、_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>

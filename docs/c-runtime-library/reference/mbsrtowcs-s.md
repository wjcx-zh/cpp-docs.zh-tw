---
title: mbsrtowcs_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbsrtowcs_s
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
- mbsrtowcs_s
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8885d11c7fca10c63077464020a8bbab2b6f3ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

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
大小*wcstr*字組 （寬字元） 中。

*mbstr*<br/>
要轉換的多位元組字元字串位置的間接指標。

*count*<br/>
將儲存在寬字元的數目上限*wcstr*緩衝區，不包括結束的 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指標**mbstate_t**轉換狀態物件。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 因為內部**mbstate_t**物件不是執行緒安全，我們建議您一律傳遞您自己*mbstate*參數。

## <a name="return-value"></a>傳回值

如果轉換成功為零，若失敗則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*wcstr*為 null 指標和*sizeInWords* > 0|**EINVAL**|
|*mbstr*為 null 指標|**EINVAL**|
|字串間接指向*mbstr*包含對目前的地區設定而言無效的多位元組序列。|**EILSEQ**|
|目的地緩衝區為太小，無法包含已轉換的字串 (除非*計數*是 **_TRUNCATE**; 如需詳細資訊，請參閱 < 備註 >)|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函數會傳回錯誤碼，並設定**errno**如下表所示。

## <a name="remarks"></a>備註

**Mbsrtowcs_s**函式所間接指向的多位元組字元字串，轉換為*mbstr*成儲存在緩衝區所指向的寬字元*wcstr*、 藉由中所包含的轉換狀態*mbstate*。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到多位元組的 null 字元

- 遇到無效的多位元組字元

- 儲存在寬字元數目*wcstr*緩衝等於*計數*。

目的地字串*wcstr*永遠是以 null 結尾，即使發生錯誤，除非*wcstr*為 null 指標。

如果*計數*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)， **mbsrtowcs_s**轉換的字串會盡量符合目的地緩衝區，同時仍留出空間給 null結束字元。

如果**mbsrtowcs_s**成功轉換來源字串中，置於已轉換的字串和 null 結束字元成寬字元大小 *&#42;pReturnValue*提供*pReturnValue*不是 null 指標。 發生這種情況即使*wcstr*引數為 null 指標，並讓您判斷所需的緩衝區大小。 請注意，如果*wcstr*為 null 指標，*計數*會被忽略。

如果*wcstr*不是 null 指標，指向的指標物件*mbstr*會指派給 null 指標，如果由於達到結束的 null 字元而停止轉換。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*mbstate* null 指標，而內部程式庫**mbstate_t**會使用轉換狀態靜態物件。 由於此內部靜態物件不是安全執行緒，我們建議您傳遞您自己*mbstate*值。

如果**mbsrtowcs_s**遇到多位元組字元不是有效的目前地區設定，它會將-1 放 *&#42;pReturnValue*，將目的緩衝區*wcstr*為空字串，設定**errno**至**EILSEQ**，並傳回**EILSEQ**。

如果指向的序列*mbstr*和*wcstr*重疊，行為**mbsrtowcs_s**是未定義。 **mbsrtowcs_s**會受到目前地區設定之 LC_TYPE 分類。

> [!IMPORTANT]
> 請確認*wcstr*和*mbstr*沒有重疊，而且*計數*會正確反映要轉換的多位元組字元數。

**Mbsrtowcs_s**函式不同於[mbstowcs_s、 _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)重新。 轉換狀態會儲存在*mbstate*的相同或其他可重新啟動的函式的後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，應用程式應該使用**mbsrlen**而不是**mbslen**，如果的後續呼叫**mbsrtowcs_s**而非**mbstowcs_s**.

C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以使用較新且安全的對應函式，來自動取代不安全的舊函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Mbsrtowcs_s**函式是安全多執行緒的目前執行緒的呼叫中沒有任何函式**setlocale** ，只要這個函式執行和*mbstate*引數不是 null 指標。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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

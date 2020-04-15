---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338906"
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

*p 傳回值*<br/>
已轉換的字元數。

*wc斯特*<br/>
緩衝區位址，要儲存產生的已轉換寬字元字串。

*大小字內*<br/>
單詞中*wcstr*的大小(寬字元)。

*姆布斯特*<br/>
要轉換的多位元組字元字串位置的間接指標。

*count*<br/>
要儲存在*wcstr*緩衝區中的最大寬字元數,不包括終止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向**mbstate_t**轉換狀態物件的指標。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是線程安全的,因此我們建議您始終傳遞自己的*mbstate*參數。

## <a name="return-value"></a>傳回值

如果轉換成功為零，若失敗則為錯誤碼。

|錯誤狀況|傳回值與**差錯**|
|---------------------|------------------------------|
|*wcstr*是空指標,*大小 InWords* > 0|**埃因瓦爾**|
|*mbstr*是空指標|**埃因瓦爾**|
|*mbstr*間接指向的字串包含一個對當前區域設置無效的多位元組序列。|**EILSEQ**|
|目標緩衝區太小,無法包含轉換後的字串(除非*計數***_TRUNCATE;** 有關詳細資訊,請參閱備註)|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將返回錯誤代碼並設置表中指示的**errno。**

## <a name="remarks"></a>備註

**mbsrtowcs_s**函數通過使用*mbstate*中包含的轉換狀態,將*mbstr*間接指向的多位元組位元字串轉換為存儲在*wcstr*指向的緩衝區中的寬字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到多位元組的 null 字元

- 遇到無效的多位元組字元

- 儲存在*wcstr*緩衝區的寬字元數等於*計數*。

目標字串*wcstr*始終為 null 終止,即使在出現錯誤的情況下也是如此,除非*wcstr*是空指標。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值 **,mbsrtowcs_s**轉換盡可能多的字串,以適應目標緩衝區,同時仍然留有空終止符的空間。

如果**mbsrtowcs_s**成功轉換源字串,它將大小以轉換後的字串和空終止符的寬字元形式放入 *&#42;pReturnValue,* 前提是*pReturnValue*不是空指標。 即使*wcstr*參數是空指標,並允許您確定所需的緩衝區大小,也會發生這種情況。 請注意,如果*wcstr*是空指標,則*忽略計數*。

如果*wcstr*不是空指標,則如果由於達到終止空字元而停止轉換,則*mbstr*指向的指針對象將分配一個空指標。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。

如果*mbstate*是空指標,則使用庫內部**mbstate_t**轉換狀態靜態物件。 由於此內部靜態物件不是線程安全的,因此我們建議您傳遞自己的*mbstate*值。

如果**mbsrtowcs_s**遇到在當前區域設定中無效的多位元組元,它將在 *&#42;pReturnValue*中放入 -1,將目標緩衝區*wcstr*設定為空字串,將**errno**設定到**EILSEQ,** 然後傳回**EILSEQ**。

如果*mbstr*和*wcstr*指向的序列重疊,則**mbsrtowcs_s**的行為未定義。 **mbsrtowcs_s**受當前區域設置的LC_TYPE類別的影響。

> [!IMPORTANT]
> 確保*wcstr*和*mbstr*不重疊,並且*該計數*正確反映要轉換的多位元組位元元數。

**mbsrtowcs_s**功能不同於[mbstowcs_s,_mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)它的可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如,如果使用後續對**mbsrtowcs_s**的調用而不是**mbstowcs_s**,則應用程式應使用**mbsrlen**而不是**mbslen。**

C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以使用較新且安全的對應函式，來自動取代不安全的舊函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

如果當前線程調用**setlocale**中沒有函數,只要此函數正在執行並且*mbstate*參數不是空指標,則**mbsrtowcs_s**函數是多線程安全的。

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

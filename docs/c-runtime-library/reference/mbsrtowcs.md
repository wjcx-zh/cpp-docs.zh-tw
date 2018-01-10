---
title: mbsrtowcs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbsrtowcs
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
f1_keywords: mbsrtowcs
dev_langs: C++
helpviewer_keywords: mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b51f8ccbac43e30202598499613d3b1c7c6e0a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mbsrtowcs"></a>mbsrtowcs
將目前地區設定的多位元組字元字串轉換成對應的寬字元字串，並提供在多位元組字元中間重新啟動的功能。 這個函式已有更安全的版本可用，請參閱 [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 [輸出] `wcstr`  
 用來儲存所產生之已轉換寬字元字串的位址。  
  
 [in、out] `mbstr`  
 要轉換之多位元組字元字串位置的間接指標。  
  
 [in] `count`  
 要轉換並儲存在 `wcstr` 中的最大字元數 (而不是位元組)。  
  
 [in、out] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。 如果此值為 null 指標，會使用靜態內部轉換狀態物件。 因為內部 `mbstate_t` 物件不是安全執行緒，我們建議您一律傳遞您自己的 `mbstate` 參數。  
  
## <a name="return-value"></a>傳回值  
 傳回成功轉換的字元數，但不包含結束的 null 字元 (如果有的話)。 如果發生錯誤，則傳回 (size_t)(-1)，並將 `errno` 設為 EILSEQ。  
  
## <a name="remarks"></a>備註  
 `mbsrtowcs` 函式會透過 `mbstr` 中包含的轉換狀態，將 `wcstr` 所間接指向的多位元組字元字串，轉換成儲存在緩衝區中由 `mbstate` 所指向的寬字元。 繼續為每個字元轉換，直到遇到結束的 null 多位元組字元、遇到未對應至目前地區設定之有效字元的多位元組序列，或直到已轉換 `count` 個字元。 如果 `mbsrtowcs` 在發生 `count` 之前或期間遇到 null 多位元組字元 ('\0')，則會將字元轉換成 16 位元結束的 null 字元並停止。  
  
 因此，如果 `wcstr` 在轉換期間遇到 null 多位元組字元，則 `mbsrtowcs` 的寬字元字串只能以 null 結束。 如果 `mbstr` 和 `wcstr` 所指向的序列重疊，`mbsrtowcs` 的行為不明。 `mbsrtowcs` 受到目前地區設定之 LC_TYPE 分類的影響。  
  
 `mbsrtowcs` 函式的重新啟動能力與 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) 不同。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用 `mbsrlen` 的後續呼叫，而不是 `mbslen`，應用程式應該使用 `mbsrtowcs`，而不是 `mbstowcs.`。  
  
 如果 `wcstr` 不是 null 指標，並由於達到結束的 null 字元而停止轉換，則會將 null 指標指派給 `mbstr` 所指向的指標物件。 否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 (如果有的話)。 這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。  
  
 如果 `wcstr` 引數是 null 指標，則會忽略 `count` 引數，並且 `mbsrtowcs` 會傳回目的地字串所需的寬字元大小。 如果 `mbstate` 是 null 指標，函式會使用非安全執行緒靜態內部 `mbstate_t` 轉換狀態物件。 如果字元序列 `mbstr` 沒有對應的多位元組字元表示法，則傳回 -1，並將 `errno` 設為 `EILSEQ`。  
  
 如果 `mbstr` 為 null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 -1。  
  
 在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>例外狀況  
 `mbsrtowcs` 函式是安全多執行緒，但前提是目前執行緒中必須沒有任何函式呼叫 `setlocale`、這個函式必須正在執行，且 `mbstate` 引數不得為 null 指標。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`mbsrtowcs`|\<wchar.h>|  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
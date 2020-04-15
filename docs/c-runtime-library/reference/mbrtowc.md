---
title: mbrtowc
ms.date: 4/2/2020
api_name:
- mbrtowc
- _o_mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: be46c3f3c728b70c7cbf060572acc24662637a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340922"
---
# <a name="mbrtowc"></a>mbrtowc

將目前地區設定的多位元組字元轉換成對等的寬字元，並提供在多位元組字元中間重新啟動的功能。

## <a name="syntax"></a>語法

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>參數

*瓦查爾*<br/>
寬字元的位址以接收轉換的寬字元字串(**類型wchar_t**)。 如果不需要傳回任何寬字元，這個值可以是 null 指標。

*姆布查爾*<br/>
位元組序列 (多位元組字元) 的位址。

*count*<br/>
要檢查的位元組數目。

*mbstate*<br/>
轉換狀態物件的指標。 如果這個值是 null 指標，函式會使用靜態內部轉換狀態物件。 由於內部**mbstate_t**物件不是線程安全的,因此我們建議您始終傳遞自己的*mbstate*參數。

## <a name="return-value"></a>傳回值

下列其中一個值：

0 下一*個計數*或更少位元組完成表示空寬字元的多位元組字元,如果*wchar*不是空指標,該字元存儲在*wchar*中。

1 表示*計數*,包括下一個*計數*或更少的位元組完成有效的多位元組位元元。 傳回的值是完成多位元組字元的位元組數目。 如果*wchar*不是空指標,則寬字元等效項存儲在*wchar*中。

(size_t)(-1)發生編碼錯誤。 下一個*計數*或更少的位元組不會貢獻為完整且有效的多位元組位元元。 在這種情況下 **,errno**設置為 EILSEQ,並且未指定*mbstate*的轉換移位狀態。

(size_t)(-2)下一個*計數*位元組將貢獻為不完整但可能有效的多位元組位元元,並且所有*計數*位元組都已處理。 *wchar*中不儲存任何值,但*mbstate*將更新以重新啟動函數。

## <a name="remarks"></a>備註

如果*mbchar*是空指標,則函數等效於呼叫:

`mbrtowc(NULL, "", 1, &mbstate)`

在這種情況下,將忽略參數*wchar*和*count*的值。

如果*mbchar*不是空指標,則函數將檢查*mbchar*中的*計數*位元組,以確定完成下一個多位元元元元所需的位元組數。 如果下一個字元有效,則相應的多位元組字元存儲在*wchar*中(如果它不是空指標)。 如果字元是相應的寬空字元,則生成的*mbstate*狀態為初始轉換狀態。

**mbrtowc**函數與[mbtowc不同,_mbtowc_l](mbtowc-mbtowc-l.md)其可重新啟動性。 轉換狀態以*mbstate*儲存,用於後續對相同或其他可重新啟動函數的調用。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如,如果使用後續對**wcsrtombs**的調用而不是**wcstombs,** 則應用程式應使用**wcsrlen**而不是**wcslen。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="example"></a>範例

將多位元組字元轉換成其對等的寬字元。

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>範例輸出

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>

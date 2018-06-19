---
title: mbrtowc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbrtowc
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
- mbrtowc
dev_langs:
- C++
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 256c3df754607d0d9321f87d565e2ce94491035c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405311"
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

*wchar*<br/>
接收已轉換寬字元字串的寬字元的位址 (型別**wchar_t**)。 如果不需要傳回任何寬字元，這個值可以是 null 指標。

*mbchar*<br/>
位元組序列 (多位元組字元) 的位址。

*count*<br/>
要檢查的位元組數目。

*mbstate*<br/>
轉換狀態物件的指標。 如果這個值是 null 指標，函式會使用靜態內部轉換狀態物件。 因為內部**mbstate_t**物件不是執行緒安全，我們建議您一律傳遞您自己*mbstate*引數。

## <a name="return-value"></a>傳回值

下列其中一個值：

0 的下一步*計數*或更少個位元組會完成代表 null 寬字元，會儲存在多位元組字元*wchar*，如果*wchar*不是 null 指標。

1 到*計數*(含） 之間的下一步*計數*或較少位元組完成有效多位元組字元。 傳回的值是完成多位元組字元的位元組數目。 對等的寬字元會儲存在*wchar*，如果*wchar*不是 null 指標。

(size_t)(-1)發生編碼錯誤。 下一步*計數*或較少位元組不會產生完整且有效的多位元組字元。 在此情況下， **errno**設為 EILSEQ，且在轉換移位狀態*mbstate*未指定。

(size_t)(-2)下一步*計數*個位元組會產生不完整但可能有效的多位元組字元，而且所有*計數*已處理的位元組。 沒有值儲存在*wchar*，但*mbstate*會更新，以重新啟動函式。

## <a name="remarks"></a>備註

如果*mbchar*為 null 指標，函式相當於呼叫：

`mbrtowc(NULL, "", 1, &mbstate)`

在此情況下，將引數值*wchar*和*計數*都會被忽略。

如果*mbchar*不是 null 指標，函式會檢查*計數*位元組從*mbchar*來判斷所需的完成下一個所需的位元組數目多位元組字元。 如果下一個字元是有效的對應的多位元組字元會儲存在*wchar*如果不是 null 指標。 如果字元是對應的 null 寬字元，產生的狀態*mbstate*是初始轉換狀態。

**Mbrtowc**函式不同於[mbtowc、 _mbtowc_l](mbtowc-mbtowc-l.md)重新。 轉換狀態會儲存在*mbstate*的相同或其他可重新啟動的函式的後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，應用程式應該使用**wcsrlen**而不是**wcslen**如果的後續呼叫**wcsrtombs**而非**wcstombs**.

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

|常式|必要的標頭|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>

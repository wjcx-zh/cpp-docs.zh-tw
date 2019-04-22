---
title: '#行指示詞 (C /C++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: ad0fe1514e89b861bab046652b1768862cc8045b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023733"
---
# <a name="line-directive-cc"></a>#line 指示詞 (C/C++)

**#Line**指示詞會指示前置處理器將編譯器內部儲存的行號和檔名變更為指定的行號和檔名。

## <a name="syntax"></a>語法

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>備註

編譯器會使用這個行號和選擇性檔名來指向它在編譯期間發現的錯誤。 行號通常參考目前的輸入行，檔名則參考目前的輸入檔。 每次一行程式碼處理後，行號會遞增。

*數字序列*值可以是任何整數常數。 在前置處理語彙基元上可以執行巨集取代，不過結果必須評估為正確的語法。 *檔名*可以是任意字元的組合，而且必須括在雙引號 (**"」**)。 如果*filename*已省略前, 一個檔名維持不變。

您可以藉由撰寫改變的原始程式碼行號和檔名 **#line**指示詞。 若要判斷預先定義的巨集值翻譯工具使用的行號和檔名`__FILE__`和`__LINE__`。 您可以使用這些巨集，將自述性的錯誤訊息插入程式文字中。 如需有關這些預先定義的巨集的詳細資訊，請參閱 <<c0> [ 預先定義巨集](../preprocessor/predefined-macros.md)。

`__FILE__`巨集會展開其內容是檔名，以雙引號括住的字串 (**""**)。

如果您變更行號和檔名，編譯器會忽略先前的值並以新的值繼續處理。 **#Line**指示詞通常可由程式產生器來會造成錯誤訊息參考到產生的程式而不是原始程式檔。

下列範例說明 **#line**並`__LINE__`和`__FILE__`巨集。

在此陳述式中，內部儲存的行號被設為 151，檔案名稱變更為 copy.c。

```cpp
#line 151 "copy.c"
```

在此範例中，巨集會`ASSERT`會使用預先定義的巨集`__LINE__`和`__FILE__`列印有關原始程式檔的錯誤訊息，如果指定的判斷提示不是 true。

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)
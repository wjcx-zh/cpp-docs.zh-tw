---
title: '#line 指示詞 (C/C++)'
description: '描述 #line 指示詞，用來設定預處理器宏所報告的行號和檔案名。'
ms.date: 07/06/2020
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 7b671cfdf5d5ce43024ac3e038c214396ac8679c
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058616"
---
# <a name="line-directive-cc"></a>#line 指示詞（C/c + +）

**#Line**指示詞會告訴預處理器將行號和檔案名的編譯器報告值設定為指定的行號和檔案名。

## <a name="syntax"></a>Syntax

> **`#line`***數位-序列*["*filename*"]

## <a name="remarks"></a>備註

編譯器會使用這個行號和選擇性檔名來指向它在編譯期間發現的錯誤。 行號通常參考目前的輸入行，檔名則參考目前的輸入檔。 每次一行程式碼處理後，行號會遞增。

*數位序列*值可以是任何整數常數。 宏取代可以用於前置處理標記，但結果必須評估為正確的語法。 *檔案名*可以是任何字元的組合，而且必須以雙引號（）括住 `" "` 。 如果省略*filename* ，則先前的檔案名會保持不變。

您可以藉由撰寫指示詞來改變原始程式列號和檔案名 **`#line`** 。 **`#line`** 指示詞會設定緊接在原始程式檔中指示詞後面的那一行的值。 翻譯工具會使用行號和檔案名來判斷預先定義宏和的值 `__FILE__` `__LINE__` 。 您可以使用這些巨集，將自述性的錯誤訊息插入程式文字中。 如需這些預先定義宏的詳細資訊，請參閱[預先定義的宏](../preprocessor/predefined-macros.md)。

`__FILE__`宏會展開為字串，其內容為檔案名，以雙引號（）括住 `" "` 。

如果您變更行號和檔名，編譯器會忽略先前的值並以新的值繼續處理。 程式產生器通常會使用 **#line**指示詞。 它是用來導致錯誤訊息參考原始來源檔案，而不是產生的程式。

## <a name="example"></a>範例

下列範例說明 **`#line`** 和 `__LINE__` 和 `__FILE__` 宏。

在第一個範例中，行號設定為10，然後設為20，而 filename 則變更為*hello .cpp*。

```cpp
// line_directive.cpp
// Compile by using: cl /W4 /EHsc line_directive.cpp
#include <stdio.h>

int main()
{
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 10
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 20 "hello.cpp"
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
}
```

```Output
This code is on line 7, in file line_directive.cpp
This code is on line 10, in file line_directive.cpp
This code is on line 20, in file hello.cpp
This code is on line 21, in file hello.cpp
```

在此範例中，宏會 `ASSERT` 使用預先定義的宏 `__LINE__` ，並在 `__FILE__` 指定的判斷提示不是 true 時，列印有關原始程式檔的錯誤訊息。

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)

---
title: '#line 指示詞 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220233"
---
# <a name="line-directive-cc"></a>#line 指示詞 (CC++/)

**#Line**指示詞會告訴預處理器將編譯器內部儲存的行號和檔案名變更為指定的行號和檔案名。

## <a name="syntax"></a>語法

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>備註

編譯器會使用這個行號和選擇性檔名來指向它在編譯期間發現的錯誤。 行號通常參考目前的輸入行，檔名則參考目前的輸入檔。 每次一行程式碼處理後，行號會遞增。

*數位序列*值可以是任何整數常數。 在前置處理語彙基元上可以執行巨集取代，不過結果必須評估為正確的語法。 *檔案名*可以是任何字元的組合, 而且必須以雙引號 (`" "`) 括住。 如果省略*filename* , 則先前的檔案名會保持不變。

您可以藉由撰寫 **#line**指示詞來改變原始程式列號和檔案名。 翻譯工具會使用行號和檔案名來判斷預先定義宏`__FILE__`和`__LINE__`的值。 您可以使用這些巨集，將自述性的錯誤訊息插入程式文字中。 如需這些預先定義宏的詳細資訊, 請參閱[預先定義的宏](../preprocessor/predefined-macros.md)。

宏會展開為字串, 其內容為檔案名, 以雙引號 (`" "`) 括住。 `__FILE__`

如果您變更行號和檔名，編譯器會忽略先前的值並以新的值繼續處理。 程式產生器通常會使用 **#line**指示詞, 讓錯誤訊息參考原始來源檔案, 而不是產生的程式。

下列範例說明 **#line**和`__LINE__`和`__FILE__`宏。

在此語句中, 內部儲存的行號會設定為 151, 而檔案名會變更為 copy. c。

```C
#line 151 "copy.c"
```

在此範例中, 宏`ASSERT`會使用預先定義`__LINE__`的`__FILE__`宏, 並在指定的判斷提示不是 true 時, 列印有關原始程式檔的錯誤訊息。

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)

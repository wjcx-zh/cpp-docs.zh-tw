---
title: 語彙基元帶入的運算子 (##)
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 4bf1b8c8f56ab9375503c9e8fb6a906706fc70bb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218112"
---
# <a name="token-pasting-operator-"></a>語彙基元帶入的運算子 (##)

雙數位記號或*標記貼入*的運算子 ( **##** ), 有時稱為*合併*或*組合*運算子, 會用於類似物件和類似函式的宏。 它允許將不同的權杖聯結為單一權杖, 因此, 不能是巨集定義中的第一個或最後一個 token。

如果巨集定義中的開頭是型式參數，後方接著語彙基元帶入的運算子，則會立即以未展開的實際引數取代型式參數。 巨集展開會在引數取代之後才執行。

然後, 會移除*權杖-字串*中每個出現的標記貼上運算子, 並串連其前面和後面的權杖。 產生的語彙基元必須是有效的語彙基元。 如果是的話，則會掃描語彙基元中是否存在代表巨集名稱的取代項目。 識別項會表示名稱，因此可在取代之前知悉程式中串連的語彙基元。 每一個語彙基元表示在其他位置定義 (可能是在程式或編譯器命令列中) 的語彙基元。 在運算子前方或後方的空白字元為選擇項。

這個範例示範如何在指定程式輸出時使用字串化和語彙基元帶入的運算子：

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

如果使用如下的數值引數呼叫巨集

```cpp
paster( 9 );
```

巨集會產生

```cpp
printf_s( "token" "9" " = %d", token9 );
```

會變成

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>範例

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>另請參閱

[預處理器運算子](../preprocessor/preprocessor-operators.md)

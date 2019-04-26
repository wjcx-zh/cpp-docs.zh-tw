---
title: 語彙基元帶入的運算子 (##)
ms.date: 11/04/2016
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: dab4da5fd65fc280d2061256a580a015917d24b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179590"
---
# <a name="token-pasting-operator-"></a>語彙基元帶入的運算子 (##)

雙精度浮點數字符號或 「 語彙基元帶入 」 的運算子 (**##**)，有時稱為 「 合併 」 運算子，會在類似物件和函式類似巨集。 它可讓不同的語彙基元聯結成單一語彙基元，因此不可以是巨集定義中的第一個或最後一個語彙基元。

如果巨集定義中的開頭是型式參數，後方接著語彙基元帶入的運算子，則會立即以未展開的實際引數取代型式參數。 巨集展開會在引數取代之後才執行。

然後，每個中的語彙基元帶入運算子的次數*語彙基元字串*移除時，和前方及後方的語彙基元會串連。 產生的語彙基元必須是有效的語彙基元。 如果是的話，則會掃描語彙基元中是否存在代表巨集名稱的取代項目。 識別項會表示名稱，因此可在取代之前知悉程式中串連的語彙基元。 每一個語彙基元表示在其他位置定義 (可能是在程式或編譯器命令列中) 的語彙基元。 在運算子前方或後方的空白字元為選擇項。

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

[前置處理器運算子](../preprocessor/preprocessor-operators.md)
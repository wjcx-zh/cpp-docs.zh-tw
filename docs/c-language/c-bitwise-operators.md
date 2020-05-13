---
title: C 位元運算子
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168769"
---
# <a name="c-bitwise-operators"></a>C 位元運算子

位運算子會執行位 AND （**&**）、位互斥 or （**^**）和位包含 or （**&#124;**）運算。

## <a name="syntax"></a>語法

*和-* expression： &nbsp; &nbsp;*等號運算式* &nbsp; &nbsp;*和運算式* **&** *等號*運算式

*互斥 or*運算式： &nbsp; &nbsp;*和運算式* &nbsp; &nbsp;*互斥 or* **^** *運算式*

*內含 or 運算式*： &nbsp; &nbsp;*獨佔* &nbsp; &nbsp;或運算式*內含*或運算式 &#124;*互斥或*運算式

位元運算子的運算元必須是整數類型，但其類型可以不同。 這些運算子會執行一般算術轉換；結果類型是運算元在轉換之後的類型。

C 位元運算子描述如下：

|運算子|描述|
|--------------|-----------------|
|**&**|位元 AND 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果這兩個位元都是 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。|
|**^**|位元互斥 OR 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果一個位元為 0 而另一個位元為 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。|
|**&#124;**|位元包含 OR 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果其中一個位元是 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。|

## <a name="examples"></a>範例

下列三個範例使用這些宣告：

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

指派給第一個範例中 `n` 的結果與 `i` (0xAB00 十六進位) 相同。

```C
n = i | j;

n = i ^ j;
```

第二個範例中的位元包含 OR 會產生值 0xABCD (十六進位)，而第三個範例中的位元互斥 OR 產生 0xCD (十六進位)。

**Microsoft 特定的**

在帶正負號的整數上執行位元運算的結果是根據 ANSI C 標準實作定義。 針對 Microsoft C 編譯器，帶正負號整數的位元運算運作方式，與不帶正負號整數的位元運算相同。 例如，`-16 & 99` 可以用二進位運算式表示為

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

位元 AND 的結果是 96 (十進位)。

**結束 Microsoft 專有**

## <a name="see-also"></a>請參閱

[位元 AND 運算子：&](../cpp/bitwise-and-operator-amp.md)<br/>
[位互斥 OR 運算子： ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[位元包含 OR 運算子：&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)

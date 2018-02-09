---
title: "C 位元運算子 | Microsoft Docs"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81498cfcc2dc93c407bfde5e9d832a9abdeab970
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="c-bitwise-operators"></a>C 位元運算子

位元運算子會執行位元 AND (**&**)、位元互斥 OR (**^**) 與 bitwise-inclusive-OR (**&#124;**) 運算。

## <a name="syntax"></a>語法

*AND-expression*：  
&nbsp;&nbsp;*equality-expression*  
&nbsp;&nbsp;*AND-expression* **&** *equality-expression*

*exclusive-OR-expression*：  
&nbsp;&nbsp;*AND-expression*  
&nbsp;&nbsp;*exclusive-OR-expression* **^** *AND-expression*

*inclusive-OR-expression*：  
&nbsp;&nbsp;*exclusive-OR-expression*  
&nbsp;&nbsp;*inclusive-OR-expression* &#124; *exclusive-OR-expression*

位元運算子的運算元必須是整數類型，但其類型可以不同。 這些運算子會執行一般算術轉換；結果類型是運算元在轉換之後的類型。

C 位元運算子描述如下：

|運算子|描述|
|--------------|-----------------|
|**&**|位元 AND 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果兩個位元皆為 1，則對應的結果位元會設為 1。 否則，對應結果位元會設為 0。|
|**^**|位元互斥 OR 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果其中一個位元為 0，而另一個位元為 1，則會將對應的結果位元設為 1。 否則，對應結果位元會設為 0。|
|**&#124;**|位元包含 OR 運算子會比較其第一個運算元的每個位元，以及其第二個運算元的對應位元。 如果任一位元為 1，則對應結果位元會設為 1。 否則，對應結果位元會設為 0。|

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

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[位元 AND 運算子：&](../cpp/bitwise-and-operator-amp.md)  
[位元互斥 OR 運算子：^](../cpp/bitwise-exclusive-or-operator-hat.md)  
[位元包含 OR 運算子：&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)  
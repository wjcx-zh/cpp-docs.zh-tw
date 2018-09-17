---
title: 傳遞的參數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8db6b61936b2122cd984e594c1ff3f162fa3dfe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724447"
---
# <a name="parameter-passing"></a>參數傳遞

前四個整數引數會傳入暫存器。 整數值會在 RCX、 RDX、 R8 和 R9 中傳遞 （依順序由左到右）。 引數 5 和更新版本會在堆疊上傳遞。 所有引數會在暫存器中靠右對齊。 這是讓被呼叫者可以略過暫存器的較高的位元，如果需要而且可以存取所需的暫存器使用的部份。

浮點數和雙精確度引數會傳遞在 XMM0 中-XMM3 （最多 4) 與一般的基線位置所使用的整數插槽 （RCX RDX、 R8 和 R9），略過 （請參閱範例），反之亦然。

[__m128](../cpp/m128.md)類型、 陣列和字串一律不會以即時運算值傳遞，但而是將指標傳遞至呼叫端所配置的記憶體。 結構/等位的大小為 8、 16、 32 或 64 位元和 __m64 會傳遞，如同它們是相同大小的整數。 這些大小以外的結構/等位的指標傳遞至呼叫端所配置的記憶體。 這些彙總類型傳遞的指標 (包括\__m128)，呼叫端配置的暫存記憶體將會對齊 16 位元組。

未配置堆疊空間，並不會呼叫其他函式的內建函式可以使用其他動態暫存器，來傳遞其他暫存器引數，因為編譯器和內建函式實作之間的緊密繫結。 這是進一步改善效能的機會。

被呼叫者有責任的傾印到其陰影空間，如有需要的暫存器參數。

下表摘要說明如何傳遞參數：

|參數類型|如何傳遞|
|--------------------|----------------|
|浮點|第一次參數 4-透過 XMM3 XMM0。 其他項目堆疊上傳遞。|
|整數|前 4 個參數-RCX，RDX，R8 R9。 其他項目堆疊上傳遞。|
|彙總 （8、 16、 32、 或 64 位元） 及 __m64|前 4 個參數-RCX，RDX，R8 R9。 其他項目堆疊上傳遞。|
|彙總 （其他）|指標。 作為指標在 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|
|__m128|指標。 作為指標在 RCX、 RDX、 R8 和 R9 中傳遞的前 4 個參數|

## <a name="example-of-argument-passing-1---all-integers"></a>傳遞 1-所有整數引數的範例

```
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

## <a name="example-of-argument-passing-2---all-floats"></a>引數傳遞 2-所有的浮點數的範例

```
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>引數傳遞 3-混合式的整數和浮點數的範例

```
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>範例中的引數傳遞 4-__m64、 \__m128，和彙總

```
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)
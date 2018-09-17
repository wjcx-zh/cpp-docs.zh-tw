---
title: 傳回值 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 673853417ad3dd5f08171ea2d5b55df5440705ad
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714632"
---
# <a name="return-values-c"></a>傳回值 (C++)

可納入 64 位元的純量傳回值將會透過 RAX 傳回，其中包括 __m64 類型。 非純量類型包括浮點數、 雙精度浮點數和向量類型，例如[__m128](../cpp/m128.md)， [__m128i](../cpp/m128i.md)， [__m128d](../cpp/m128d.md) XMM0 中傳回。 對於 RAX 或 XMM0 中傳回的值，其中未使用之位元的狀態尚未定義。

使用者定義的類型可透過全域函式和靜態成員函式的值傳回。 使用者定義的類型若要由 RAX 中的值傳回，其長度必須為 1、2、4、8、16、32 或 64 個位元；沒有使用者定義的建構函式、解構函式或複製指派運算子；沒有私用或受保護的非靜態資料成員；沒有參考類型的非靜態資料成員；沒有基底類別；沒有虛擬函式；亦沒有不符合這些需求的資料成員。 (這基本上是 C++03 POD 類型的定義。 因為在 C++11 標準中的定義已經變更，所以我們不建議將 `std::is_pod` 用於這項測試。)否則，呼叫端會負責配置記憶體，並且為傳回值傳遞一個指標做為第一個引數。 後續的引數將向右移一個引數。 在 RAX 中的被呼叫端必須傳回相同的指標。

這些範例展示有指定之宣告的函式如何傳遞參數和傳回值：

## <a name="example-of-return-value-1---64-bit-result"></a>傳回值 1-64 位元結果的範例

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

## <a name="example-of-return-value-2---128-bit-result"></a>傳回值 2-128 位元結果的範例

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>傳回值 3-由指標產生使用者類型結果的範例

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

## <a name="example-of-return-value-4---user-type-result-by-value"></a>傳回值 4-依值的使用者類型結果的範例

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)
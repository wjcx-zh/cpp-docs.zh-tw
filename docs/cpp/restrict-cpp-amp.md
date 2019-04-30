---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 3609e3f0541cfd8a8af8559d8d49e6a77c00d91c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403382"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

限制規範可以套用到函式和 Lambda 宣告。 它會在函式中的程式碼上強制執行限制，以及在使用 C++ Accelerated Massive Parallelism (C++ AMP) 的應用程式中函式的行為上強制執行限制。

> [!NOTE]
>  如需**限制**屬於關鍵字 **__declspec**儲存類別屬性，請參閱[限制](../cpp/restrict.md)。

**限制**子句的格式如下：

|子句|描述|
|------------|-----------------|
|`restrict(cpu)`|函式可以使用完整的 C++ 語言。 只有使用 restrict(cpu) 函式宣告的其他函式可以呼叫函式。|
|`restrict(amp)`|函式只能使用 C++ AMP 可以加速之 C++ 語言的子集。|
|`restrict(cpu)` 和 `restrict(amp)` 的序列。|函式必須同時符合 `restrict(cpu)` 和 `restrict(amp)` 的限制。 函式可由使用 `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)` 或 `restrict(amp, cpu)` 宣告的函式呼叫。<br /><br /> `restrict(A) restrict(B)` 格式可以撰寫為 `restrict(A,B)`。|

## <a name="remarks"></a>備註

**限制**關鍵字是內容關鍵字。 限制規範、`cpu` 和 `amp` 不是保留字。 規範的清單無法擴充。 函式沒有**限制**子句是函式具有相同`restrict(cpu)`子句。

內含 `restrict(amp)` 子句的函式具有下列限制：

- 函式只會呼叫內含 `restrict(amp)` 子句的函式。

- 函式必須為可內嵌。

- 函式只可以宣告**int**，**不帶正負號的 int**， **float**，並**double**變數和類別和結構，其中只包含這些型別。 **bool**也允許，但它必須是 4 位元組對齊若複合類型中使用它。

- Lambda 函式無法透過參考方式擷取，也無法擷取指標。

- 參考和單一間接取值指標只支援區域變數、函式引數和傳回型別。

- 不允許使用下列各項：

   - 遞迴。

   - 以宣告的變數[volatile](../cpp/volatile-cpp.md)關鍵字。

   - 虛擬函式。

   - 函式的指標。

   - 成員函式的指標。

   - 結構中的指標。

   - 指標的指標。

   - **goto**陳述式。

   - 標記陳述式。

   - **請嘗試**，**攔截**，或**擲回**陳述式。

   - 全域變數。

   - 靜態變數。 使用[tile_static 關鍵字](../cpp/tile-static-keyword.md)改。

   - **dynamic_cast**轉換 （cast)。

   - **Typeid**運算子。

   - asm 宣告。

   - Varargs。

如需函式限制的討論，請參閱 <<c0> [ 限制 (amp) 限制](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/)。

## <a name="example"></a>範例

下列範例示範如何使用`restrict(amp)`子句。

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
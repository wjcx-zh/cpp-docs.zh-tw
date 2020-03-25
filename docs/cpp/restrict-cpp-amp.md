---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: a100ece1a0c67be01b31f38bdca17e78c2e1b6f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179103"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

限制規範可以套用到函式和 Lambda 宣告。 它會在函式中的程式碼上強制執行限制，以及在使用 C++ Accelerated Massive Parallelism (C++ AMP) 的應用程式中函式的行為上強制執行限制。

> [!NOTE]
>  如需屬於 **__declspec**儲存類別屬性之一部分之**restrict**關鍵字的詳細資訊，請參閱[restrict](../cpp/restrict.md)。

**Restrict**子句採用下列形式：

|子句|描述|
|------------|-----------------|
|`restrict(cpu)`|函式可以使用完整的 C++ 語言。 只有使用 restrict(cpu) 函式宣告的其他函式可以呼叫函式。|
|`restrict(amp)`|函式只能使用 C++ AMP 可以加速之 C++ 語言的子集。|
|`restrict(cpu)` 和 `restrict(amp)` 的序列。|函式必須同時符合 `restrict(cpu)` 和 `restrict(amp)` 的限制。 函式可由使用 `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)` 或 `restrict(amp, cpu)` 宣告的函式呼叫。<br /><br /> `restrict(A) restrict(B)` 格式可以撰寫為 `restrict(A,B)`。|

## <a name="remarks"></a>備註

**Restrict**關鍵字是內容關鍵字。 限制規範、`cpu` 和 `amp` 不是保留字。 規範的清單無法擴充。 沒有**限制**子句的函式與具有 `restrict(cpu)` 子句的函數相同。

內含 `restrict(amp)` 子句的函式具有下列限制：

- 函式只會呼叫內含 `restrict(amp)` 子句的函式。

- 函式必須為可內嵌。

- 函數只能宣告**int**、不**帶正負**號的 int、 **float**和**double**變數，以及僅包含這些類型的類別和結構。 也允許**bool** ，但如果您在複合類型中使用，它必須是4位元組對齊。

- Lambda 函式無法透過參考方式擷取，也無法擷取指標。

- 參考和單一間接取值指標只支援區域變數、函式引數和傳回型別。

- 不允許使用下列各項：

   - 遞迴。

   - 以[volatile](../cpp/volatile-cpp.md)關鍵字宣告的變數。

   - 虛擬函式。

   - 函式的指標。

   - 成員函式的指標。

   - 結構中的指標。

   - 指標的指標。

   - **goto**語句。

   - 標記陳述式。

   - **try**、 **catch**或**throw**語句。

   - 全域變數。

   - 靜態變數。 請改用[Tile_static 關鍵字](../cpp/tile-static-keyword.md)。

   - **dynamic_cast**轉換。

   - **Typeid**運算子。

   - asm 宣告。

   - Varargs。

如需函數限制的討論，請參閱[限制（amp）限制](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/)。

## <a name="example"></a>範例

下列範例顯示如何使用 `restrict(amp)`子句。

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

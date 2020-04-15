---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 5a0011d11e4a59c9ca3a5e18f44d4cf831b21582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366650"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

限制規範可以套用到函式和 Lambda 宣告。 它會在函式中的程式碼上強制執行限制，以及在使用 C++ Accelerated Massive Parallelism (C++ AMP) 的應用程式中函式的行為上強制執行限制。

> [!NOTE]
> 有關作為儲存類屬性的 **__declspec**一部分**的限制**關鍵字的資訊,請參閱[限制](../cpp/restrict.md)。

**限制**子句採取以下形式:

|子句|描述|
|------------|-----------------|
|`restrict(cpu)`|函式可以使用完整的 C++ 語言。 只有使用 restrict(cpu) 函式宣告的其他函式可以呼叫函式。|
|`restrict(amp)`|函式只能使用 C++ AMP 可以加速之 C++ 語言的子集。|
|`restrict(cpu)` 和 `restrict(amp)` 的序列。|函式必須同時符合 `restrict(cpu)` 和 `restrict(amp)` 的限制。 函式可由使用 `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)` 或 `restrict(amp, cpu)` 宣告的函式呼叫。<br /><br /> `restrict(A) restrict(B)` 格式可以撰寫為 `restrict(A,B)`。|

## <a name="remarks"></a>備註

**限制**關鍵字是上下文關鍵字。 限制規範、`cpu` 和 `amp` 不是保留字。 規範的清單無法擴充。 沒有**限制**子句的函數與具有子句的`restrict(cpu)`函數相同。

內含 `restrict(amp)` 子句的函式具有下列限制：

- 函式只會呼叫內含 `restrict(amp)` 子句的函式。

- 函式必須為可內嵌。

- 函數只能聲明**int、****無符號 int、float**和**double**變數,以及僅包含這些類型**float**的類和結構。 **bool**也是允許的,但如果在複合類型中使用,則必須與4位元組對齊。

- Lambda 函式無法透過參考方式擷取，也無法擷取指標。

- 參考和單一間接取值指標只支援區域變數、函式引數和傳回型別。

- 不允許使用下列各項：

  - 遞迴。

  - 使用可變關鍵字聲明的[變數](../cpp/volatile-cpp.md)。

  - 虛擬函式。

  - 函式的指標。

  - 成員函式的指標。

  - 結構中的指標。

  - 指標的指標。

  - **轉到**語句。

  - 標記陳述式。

  - **嘗試**、**捕獲**或**引發**語句。

  - 全域變數。

  - 靜態變數。 請使用[tile_static關鍵字](../cpp/tile-static-keyword.md)。

  - **dynamic_cast**演員。

  - **類型化**運算符。

  - asm 宣告。

  - Varargs。

有關功能限制的討論,請參閱[限制(和)限制](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/)。

## <a name="example"></a>範例

下面的示例演示如何使用`restrict(amp)`子 句。

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

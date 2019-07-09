---
title: 編譯器錯誤 C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693436"
---
# <a name="compiler-error-c2316"></a>編譯器錯誤 C2316

> '*class_type*': 無法攔截，因為解構函式及/或複製建構函式無法存取或已刪除

值或參考，但是複製建構函式，指派運算子，攔截到例外狀況，或兩者均已無法存取。

## <a name="remarks"></a>備註

在 Visual Studio 2015 的合規性變更進行套用至不正確的 catch 陳述式的 MFC 例外狀況衍生自這個錯誤`CException`。 因為`CException`繼承私用複製建構函式，類別和其衍生項目不複製，而不傳值方式傳遞，這也表示他們無法依值攔截。 攔截由先前會導致在執行階段未攔截的例外狀況的值攔截 MFC 例外狀況的陳述式。 現在編譯器正確地識別這種情況，並報告錯誤 C2316。 若要修正此問題，我們建議您使用 MFC TRY/CATCH 巨集，而非撰寫您自己的例外狀況處理常式。 如果不是適用於您的程式碼，請改為參考所攔截 MFC 例外狀況。

## <a name="example"></a>範例

下列範例會產生 C2316，並示範如何修正此問題：

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```

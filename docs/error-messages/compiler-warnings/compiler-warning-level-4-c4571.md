---
title: 編譯器警告 (層級 4) C4571
description: 記錄 Microsoft c + + 編譯器警告 C4571。
ms.date: 08/24/2020
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 35f2b30a8ab7cfcc27ed7aae3aedd9bc81efacc8
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898547"
---
# <a name="compiler-warning-level-4-c4571"></a>編譯器警告 (層級 4) C4571

> 參考： `catch(...)` 自 Visual C++ 7.1 之後，已變更語義， (不會再攔截 SEH) 的結構化例外狀況

`catch(...)`當您指定編譯器選項時，會為每個區塊產生 C4571 **`/EHs`** 。

## <a name="remarks"></a>備註

當您指定 **`/EHs`** 編譯器選項時， `catch(...)` 區塊不會攔截結構化例外狀況。  (零除，或 null 指標例外狀況。例如，) `catch(...)` 區塊只會捕捉明確擲回的 c + + 例外狀況。 如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。

此警告預設為關閉。  開啟這個警告以確保當您使用區塊進行編譯時， **`/EHs`** `catch (...)` 不會攔截結構化例外狀況。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

您可以透過下列其中一種方式來解析 C4571：

- **`/EHa`** 如果您仍然想要讓 `catch(...)` 區塊攔截結構化例外狀況，請使用編譯。

- 如果您不想讓 `catch(...)` 區塊攔截結構化例外狀況，但仍想要使用區塊，請不要啟用 C4571 `catch(...)` 。  您仍然可以使用結構化例外狀況處理關鍵字來攔截結構化例外狀況 **`__try`** ， (、 **`__except`** 和 **`__finally`**) 。  但是請記住，使用編譯時 **`/EHs`** ，只會在擲回 c + + 例外狀況時呼叫，而不會在發生 SEH 例外狀況時呼叫。

- `catch(...)`將區塊取代為特定 c + + 例外狀況的 catch 區塊，並選擇性地在 c + + 例外狀況處理 (**`__try`** 、和) 上加入結構化例外狀況處理 **`__except`** **`__finally`** 。   如需詳細資訊，請參閱[結構化例外狀況處理 (C/c + +) ](../../cpp/structured-exception-handling-c-cpp.md)和[ `/EH` (例外狀況處理模型) ](../../build/reference/eh-exception-handling-model.md)。

## <a name="example"></a>範例

下列範例會產生 C4571。

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```

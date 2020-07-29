---
title: 編譯器警告 (層級 1) C4530
description: Microsoft c + + 編譯器警告 C4530 的參考指南。
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: fe0a2b4c8eb881327f3e59d66e7e6941f0a2cad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230658"
---
# <a name="compiler-warning-level-1-c4530"></a>編譯器警告 (層級 1) C4530

> 使用 c + + 例外狀況處理常式，但未啟用回溯語義。 指定/EHsc

程式碼會使用 c + + 例外狀況處理，但[/ehsc](../../build/reference/eh-exception-handling-model.md)不會包含在編譯器選項中。

## <a name="remarks"></a>備註

編譯器需要 **`/EHsc`** 選項來建立遵循 c + + 標準的 c + + 程式碼，以進行例外狀況處理。 標準 c + + 回溯*語義*會指定在擲回例外狀況的位置與攔截的位置之間所建立的物件和堆疊框架，必須終結並復原其資源。 這個程式就是所謂*的回溯堆疊*。

**`/EHsc`** 選項會指示編譯器產生程式碼，以便在例外狀況通過包含的堆疊框架時，在自動儲存物件上呼叫析構函數。 *自動儲存*物件是在堆疊上配置的物件，例如本機變數。 它稱為自動儲存體，因為它會在呼叫函式時自動設定，並在傳回時自動釋放。 *堆疊框架*是呼叫函式時放在堆疊上的資料，以及其自動儲存區。

當擲回例外狀況時，它可能會在攔截到幾個堆疊框架之前進行移動。 這些堆疊框架必須展開，因為例外狀況會以反向呼叫順序傳遞它們。 每個堆疊框架中的自動儲存物件都必須終結，才能完全復原其資源。 這是函式正常傳回時自動發生的相同終結和復原程式。

當未啟用選項時，擲回函式與攔截到例外狀況的函式 **`/EHsc`** 之間的自動儲存物件不會遭到終結。 只有在或區塊中建立的自動儲存物件 **`try`** **`catch`** 會被終結，這可能會導致嚴重的資源流失和其他非預期的行為。

如果您的可執行檔中可能不會擲回任何例外狀況，您可以放心地忽略此警告。 某些程式碼可能需要其他的例外狀況處理選項。 如需詳細資訊，請參閱[/EH](../../build/reference/eh-exception-handling-model.md)。

## <a name="example"></a>範例

下列範例會產生 C4530：

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

使用編譯範例 **`/EHsc`** 以解決警告。

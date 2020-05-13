---
title: 編譯器警告 (層級 1) C4530
description: Microsoft C++編譯器警告 C4530 的參考指南。
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369789"
---
# <a name="compiler-warning-level-1-c4530"></a>編譯器警告 (層級 1) C4530

> C++使用異常處理程式,但未啟用展開語義。 指定 /EHsc

代碼使用C++異常處理,但[/EHsc](../../build/reference/eh-exception-handling-model.md)不包括在編譯器選項中。

## <a name="remarks"></a>備註

編譯器需要**`/EHsc`** C++代碼生成遵循C++異常處理標準的代碼的選項。 標準C++*展開語義*指定必須在引發異常的位置和捕獲異常的位置之間構造的物件和堆疊幀,並恢復其資源。 此過程稱為*展開堆疊*。

該**`/EHsc`** 選項告訴編譯器生成代碼,當異常通過包含堆疊幀時,在自動存儲物件上調用析構函數。 *自動存儲*物件是在堆疊上分配的物件,如局部變數。 它被稱為自動存儲,因為它在調用函數時自動分配,並在返回時自動釋放。 *堆疊幀*是調用函數時放置在堆疊上的數據及其自動存儲。

引發異常時,它可能會在捕獲之前通過多個堆疊幀。 當異常以反向調用順序通過它們時,必須解開這些堆棧幀。 必須銷毀每個堆疊幀中的自動存儲物件,以便乾淨地恢復其資源。 當函數正常返回時,它會自動發生相同的銷毀和恢復過程。

未啟用**`/EHsc`** 該選項時,在引發函數和捕獲異常的函數之間的堆疊幀中的自動存儲物件不會被銷毀。 只有**嘗試**或**捕獲**塊中創建的自動存儲物件才會被銷毀,這可能導致嚴重的資源洩漏和其他意外行為。

如果無法在可執行檔中引發異常,則可以安全地忽略此警告。 某些代碼可能需要其他異常處理選項。 有關詳細資訊,請參閱[/EH](../../build/reference/eh-exception-handling-model.md)。

## <a name="example"></a>範例

以下範例產生 C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

使用 編譯示**`/EHsc`** 例 以解決警告。

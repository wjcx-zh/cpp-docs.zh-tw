---
title: 2.4.2 sections 建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ae940e37b40cbb9c883c4d7d6bca7b0fa65520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410542"
---
# <a name="242-sections-construct"></a>2.4.2 sections 建構

**各節**指示詞會識別 noniterative 的工作共用建構，指定一組要在小組中的執行緒之間分割的建構。 由小組中的執行緒中，每個區段會執行一次。 語法**各節**指示詞時，如下所示：

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句可以是下列其中一項：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate(** *variable-list* **)**

**reduction(** *operator* **:**  *variable-list* **)**

**nowait**

每個區段前面加上**一節**指示詞，雖然**一節**指示詞是選擇性的第一個區段。 **一節**指示詞必須出現的語彙範圍內**各節**指示詞。 結尾沒有隱含的障礙**各節**建構，除非**nowait**指定。

若要限制**各節**指示詞如下所示：

- A**一節**指示詞不得出現的語彙範圍外**各節**指示詞。

- 只有一個**nowait**子句可能會出現在**各節**指示詞。

## <a name="cross-references"></a>交叉參考：

- **私用**， **firstprivate**， **lastprivate**，和**減少**子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 25 頁上。
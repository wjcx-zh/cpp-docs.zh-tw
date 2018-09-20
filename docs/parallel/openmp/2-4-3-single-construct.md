---
title: 2.4.3 單一建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81abf5324c215b9011ecbd774626a213c2eda653
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376495"
---
# <a name="243-single-construct"></a>2.4.3 single 建構

**單一**指示詞會識別指定小組 （不一定是主要執行緒） 中只有一個執行緒執行相關聯的結構化的區塊的建構。 語法**單一**指示詞時，如下所示：

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句可以是下列其中一項：

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**copyprivate (** *變數清單* **)**

**nowait**

沒有隱含的障礙之後,**單一**建構，除非**nowait**指定子句。

若要限制**單一**指示詞如下所示：

- 只有一個**nowait**子句可能會出現在**單一**指示詞。

- **Copyprivate**子句不能搭配**nowait**子句。

## <a name="cross-references"></a>交叉參考：

- **私用**， **firstprivate**，以及**copyprivate**子句，請參閱[一節 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 25 頁上。
---
title: F. 新功能和 2.0 版中的說明
ms.date: 11/04/2016
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: c8a597c6af397bd162d92a945d96409b1839e2a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657134"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 新功能和 2.0 版中的說明

本附錄摘要說明對 OpenMP C/c + + 規格中從 1.0 版移至 2.0 版的重要變更。 下列項目是加入至規格的新功能：

- OpenMP 指示詞中允許使用逗號 ([2.1 節](../../parallel/openmp/2-1-directive-format.md)上第 7 頁)。

- 新增`num_threads`子句。 此子句可讓使用者要求特定數目的平行建構的執行緒 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)上第 8 頁)。

- `threadprivate`指示詞已擴充至接受靜態的區塊範圍變數 ([一節 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md)第 23 頁)。

- C99 可變長度陣列都是完整的類型，並因此可指定任何位置完成中允許的類型，執行個體的清單`private`， `firstprivate`，並`lastprivate`子句 ([區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)上 25 頁)。

- 在平行區域中的私用變數可以標示為私人一次在巢狀指示詞 ([一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 25 頁上)。

- `copyprivate`子句加入。 它提供一個機制來使用私用變數從一小組的成員的值廣播到其他成員。 它是使用共用的變數值時提供這類共用的變數會很困難 （例如，在需要不同的變數，每個層級的遞迴函式） 的替代方案。 `copyprivate`子句只能出現在**單一**指示詞 ([一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)上 32)。

- 新增計時常式`omp_get_wtick`和`omp_get_wtime`MPI 常式類似。 這些函式所需的執行牆上的時鐘時間 ([一節 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) 44 頁上並[3.3.2 節](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)45 頁上)。

- 已新增一份實作定義行為 OpenMP C/c + + 中的附錄。 的實作都必須定義，並在這些情況下其行為的文件 ([附錄 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)上第 97 頁)。

- 若要釐清或更正先前 OpenMP API 規格的 C/c + + 中的功能，有下列變更：

   - 釐清的行為`omp_set_nested`並`omp_set_dynamic`時`omp_in_parallel`傳回非零值會是未定義 ([區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)上 39，和[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上)。

   - 釐清指示詞的巢狀結構，使用巢狀的平行時 ([一節 2.9](../../parallel/openmp/2-9-directive-nesting.md)上第 33 頁)。

   - 鎖定初始化和鎖定解構函式可以呼叫在平行區域 ([一節 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) 42 頁上並[區段 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) 42 頁上)。

   - 已新增新的範例 ([附錄 A](../../parallel/openmp/a-examples.md)上 51)。
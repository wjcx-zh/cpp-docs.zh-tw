---
title: F. 2\.0 版中的新功能及詳細說明
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215029"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 2\.0 版中的新功能及詳細說明

本附錄摘要說明從版本1.0 移至2.0 版的C++ OpenMP C/規格所做的重要變更。 下列專案是新增至規格的新功能：

- [OpenMP 指示](2-directives.md#21-directive-format)詞中允許使用逗號。

- 新增 `num_threads` 子句。 這個子句可讓使用者要求[平行結構](2-directives.md#23-parallel-construct)的特定執行緒數目。

- [Threadprivate](2-directives.md#271-threadprivate-directive)指示詞已經過擴充，可接受靜態區塊範圍變數。

- C99 可變長度陣列是完整的類型，而且可以指定任何允許的完整類型，例如 `private`、`firstprivate`和 `lastprivate` 子句的清單中（請參閱[2.7.2 一節](2-directives.md#272-data-sharing-attribute-clauses)）。

- 平列區域中的私用變數可以在 nested 指示詞中再次標示為[私](2-directives.md#2721-private)用。

- 已新增 `copyprivate` 子句。 它提供一個機制，讓您可以使用私用變數，將一個小組成員的值廣播到其他成員。 當提供這類共用變數會很棘手（例如，在需要每個層級上有不同變數的遞迴中）時，就可以使用共用變數來取代值。 [Copyprivate](2-directives.md#2728-copyprivate)子句只能出現在 `single` 指示詞上。

- 新增計時常式[omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function)和[omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function)類似 MPI 常式。 這些是執行時鐘時間的必要功能。

- 已加入附錄，其中包含 OpenMP C/C++中的實作為[定義行為](e-implementation-defined-behaviors-in-openmp-c-cpp.md)清單。 在這些情況下，需要執行來定義和記錄其行為。

- 下列變更可用於針對 C/C++的先前 OpenMP API 規格中的功能進行澄清或修正：

  - 澄清當 `omp_in_parallel` 傳回非零時， [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)和[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)的行為未定義。

  - 在使用 nested parallel 時，闡明指示詞的[嵌套](2-directives.md#29-directive-nesting)。

  - [鎖定初始化](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)和[鎖定的析構](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函數可以在平列區域中呼叫。

  - [附錄 A](a-examples.md)加入了新的範例。

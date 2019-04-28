---
title: F. 新功能和 2.0 版中的說明
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362708"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 新功能和 2.0 版中的說明

本附錄摘要說明主要的變更對 OpenMP C /C++中從 1.0 版移至 2.0 版的規格。 下列項目是加入至規格的新功能：

- 逗號可以在 OpenMP[指示詞](2-directives.md#21-directive-format)。

- 新增`num_threads`子句。 此子句可讓使用者要求特定數目的執行緒[平行建構](2-directives.md#23-parallel-construct)。

- [Threadprivate](2-directives.md#271-threadprivate-directive)指示詞已擴充至接受靜態的區塊範圍變數。

- C99 可變長度陣列都是完整類型，可以指定任何地方完整類型所允許，例如資源清單`private`， `firstprivate`，並`lastprivate`子句 (請參閱[區段 2.7.2](2-directives.md#272-data-sharing-attribute-clauses))。

- 在平行區域中的私用變數可以標示[私人](2-directives.md#2721-private)一次在巢狀指示詞。

- `copyprivate`子句加入。 它提供一個機制來使用私用變數從一小組的成員的值廣播到其他成員。 它是使用共用的變數值時提供這類共用的變數會很困難 （例如，在需要不同的變數，每個層級的遞迴函式） 的替代方案。 [Copyprivate](2-directives.md#2728-copyprivate)子句只能出現在`single`指示詞。

- 新增計時常式[omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function)並[omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) MPI 常式類似。 這些函式所執行的背景牆的時鐘時間。

- 附錄一份[的實作定義行為](e-implementation-defined-behaviors-in-openmp-c-cpp.md)OpenMP c /C++已加入。 若要定義並記錄其行為在這些情況下需要實作。

- 下列變更提供給釐清或更正功能在前一個 OpenMP API 規格中為 C /C++:

  - 釐清的行為[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)並[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)當`omp_in_parallel`傳回非零值會是未定義。

  - 已釐清[指示詞的巢狀](2-directives.md#29-directive-nesting)平行巢狀使用時。

  - [鎖定初始化](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)並[鎖定解構](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函式可以呼叫在平行區域中。

  - 已新增新的範例[附錄 A](a-examples.md)。
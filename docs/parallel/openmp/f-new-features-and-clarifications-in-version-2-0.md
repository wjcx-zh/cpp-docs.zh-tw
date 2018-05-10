---
title: F. 新功能和 2.0 版中的 說明 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e48f299e66ed1b4c075757a9cd143d0afe897db
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 新功能及 2.0 版中的說明
本附錄摘要中將 1.0 版移到 2.0 版的 OpenMP C/c + + 規格的金鑰變更。 下列項目會加入規格的新功能：  
  
-   逗號可以在 OpenMP 指示詞 ([2.1 節](../../parallel/openmp/2-1-directive-format.md)上第 7 頁)。  
  
-   新增`num_threads`子句。 這個子句可讓使用者要求特定數目的執行緒的平行建構 ([2.3 節](../../parallel/openmp/2-3-parallel-construct.md)在 8 頁面上)。  
  
-   `threadprivate`指示詞已擴充至接受靜態的區塊範圍變數 ([區段 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md)在頁面上 23)。  
  
-   C99 可變長度陣列都是完整的類型，因此您可以指定任何地方完成中允許的類型，例如清單`private`， `firstprivate`，和`lastprivate`子句 ([區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)頁面 25 上)。  
  
-   私用一次在巢狀指示詞標示在平行區域中的私用變數 ([區段 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)頁面 25 上)。  
  
-   `copyprivate`子句已加入。 它提供一個機制，從一個小組成員的值廣播到的其他成員使用私用變數。 它會提供這類共用的變數會很難 （例如，在需要不同的變數在每個層級的遞迴函式） 時，使用共用的變數值的替代方案。 `copyprivate`子句只能出現在**單一**指示詞 ([區段 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)在頁面上 32)。  
  
-   加入的計時常式`omp_get_wtick`和`omp_get_wtime`MPI 常式類似。 這些函式所需的執行牆上的時鐘時間 ([區段 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md)頁面 44 上和[第 3.3.2 節](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)在 45 頁面上)。  
  
-   已加入附錄實作所定義的行為在 OpenMP C/c + + 的清單。 實作可用來定義，並在這些情況下，其行為的文件 ([附錄 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) 97 頁面上)。  
  
-   若要釐清或更正先前 OpenMP API 規格的 C/c + + 中的功能，有下列變更：  
  
    -   釐清的行為`omp_set_nested`和`omp_set_dynamic`時`omp_in_parallel`為非零，傳回未定義 ([區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39，頁面上和[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上)。  
  
    -   釐清指示詞的巢狀結構，使用巢狀的平行時 ([區段 2.9](../../parallel/openmp/2-9-directive-nesting.md)在頁面上 33)。  
  
    -   鎖定初始化和鎖定解構函式時，才能呼叫在平行區域 ([區段 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)在頁面上 42 和[區段 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) 42 頁面上)。  
  
    -   已加入新的範例 ([附錄 A](../../parallel/openmp/a-examples.md)在頁面上 51)。
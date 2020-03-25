---
title: E. OpenMP C/C++ 中的實作定義行為
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215042"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. OpenMP C/C++ 中的實作定義行為

本附錄摘要說明在此 API 中描述為「執行定義」的行為。  每個行為都會在主要規格中交叉參考回其描述。

## <a name="remarks"></a>備註

在這些情況下，需要執行來定義和記錄其行為，但這份清單可能不完整。

- **執行緒數目：** 如果在停用執行緒數目的動態調整時遇到平列區域，而且針對平列區域所要求的執行緒數目大於執行時間系統可以提供的數目，則程式的行為會是已定義的（請參閱第9頁）。

   在 Visual C++中，若為非嵌套的平列區域，則會提供64個執行緒（最大值）。

- **處理器數目：** 在任何指定時間實際裝載執行緒的實體處理器數目，都是「執行定義」（請參閱第10頁）。

   在 Visual C++中，此數位不是常數，而且是由作業系統所控制。

- **建立執行緒的小組：** 小組中執行嵌套平列區域的執行緒數目是由實作為定義（請參閱第10頁）。

   在 Visual C++中，這個數位是由作業系統決定。

- **排程（執行時間）：** 排程的相關決策會延後到執行時間。 您可以藉由設定 `OMP_SCHEDULE` 環境變數，在執行時間選擇排程類型和區塊大小。 如果未設定此環境變數，則產生的排程為「執行定義」（請參閱第13頁）。

   在 [ C++視覺效果] 中，[排程類型] 是 `static`，沒有區塊大小。

- **預設排程：** 如果沒有 schedule 子句，預設排程是「執行定義」（請參閱第13頁）。

   在 Visual C++中，預設的排程類型是 `static`，沒有區塊大小。

- 不可部分完成 **：** 它的實作為定義，是要將所有 `atomic` 指示詞取代為具有相同唯一名稱 `critical` 指示詞（請參閱第20頁）。

   在 Visual C++中，如果[由不可部分完成修改的資料](reference/openmp-directives.md#atomic)不是自然對齊，或者它是一或兩個位元組，則滿足該屬性的全部不可部分完成作業將會使用一個重要區段。 否則，將不會使用重要區段。

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function)：** 如果使用者尚未明確設定執行緒數目，則預設值為「執行定義」（請參閱第9頁）。

   在 Visual C++中，執行緒的預設數目等於處理器的數目。

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)：** 動態執行緒調整的預設值是「執行定義」。

   在 Visual C++中，預設值為 `FALSE`。

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)：** 啟用「嵌套平行處理原則」時，用來執行「嵌套平列區域」的執行緒數目是實值定義。

   在 Visual C++中，執行緒的數目是由作業系統決定。

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境變數：此環境變數的預設值為「執行定義」。

   在 [ C++視覺效果] 中，[排程類型] 是 `static`，沒有區塊大小。

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數：如果未指定 `OMP_NUM_THREADS` 環境變數的值，或者指定的值不是正整數，或如果值大於系統可支援的執行緒數目上限，則要使用的執行緒數目是由實值所定義。

   在視覺C++效果中，如果指定的值為零或更少，則執行緒的數目等於處理器的數目。  如果值大於64，則執行緒數目為64。

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數：預設值為「執行定義」。

   在 Visual C++中，預設值為 `FALSE`。

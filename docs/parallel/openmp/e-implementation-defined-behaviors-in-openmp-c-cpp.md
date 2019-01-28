---
title: E. 實作定義行為在 OpenMP C/c + +
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087219"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. 實作定義行為在 OpenMP C/c + +

本附錄摘要說明之所以被形容為 「 實作定義 「 此 API 中的行為。  每個行為是交互參考它的主要規格的說明。

## <a name="remarks"></a>備註

的實作都必須定義，並在這些情況下，其行為的文件，但這份清單可能不完整。

- **執行緒的數目：** 如果在平行區域為止已停用動態調整執行緒數目，而要求的平行區域的執行緒數目大於可以提供執行階段系統的數字，該程式的行為是實作定義 （請參閱第 9 頁）。

   Visual c + + 中，在非巢狀平行區域，64 個執行緒 （最大值） 會提供。

- **處理器數目：** 實體處理器實際上裝載在任何指定時間的執行緒數目是實作定義 （請參閱第 10 頁）。

   Visual c + + 中，這個號碼不變，，由作業系統所控制。

- **建立小組的執行緒：** 在小組執行巢狀平行區域的執行緒數目是實作定義 （請參閱第 10 頁）。

   Visual c + + 中，這個數字是由作業系統決定。

- **schedule （runtime):** 排程的相關決定會延後到執行階段。 可以在執行階段選擇的排程類型與區塊大小，藉由設定`OMP_SCHEDULE`環境變數。 如果未設定這個環境變數，產生的排程會實作定義 （請參閱分頁 13）。

   在 Visual c + +、 排程類型是`static`沒有區塊大小。

- **預設排程：** 如果沒有排程子句，預設排程是實作定義 （請參閱分頁 13）。

   在 Visual c + + 中，預設的排程類型是`static`沒有區塊大小。

- **不可部分完成：** 它是由實作定義是否實作會取代所有`atomic`指示詞與`critical`具有相同的唯一名稱 （請參閱頁面 20） 的指示詞。

   Visual c + + 中，如果修改的資料[不可部分完成](reference/openmp-directives.md#atomic)不在自然對齊或很長一或兩個位元組，如果滿足該屬性的所有不可部分完成作業會使用一個重要區段。 否則，不會使用重要區段。

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** 如果使用者尚未明確設定的執行緒數目，預設值是實作定義 （請參閱第 9 頁）。

   Visual c + + 中，預設的執行緒數目等於處理器數目。

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** 執行緒的動態調整的預設值是由實作定義。

   Visual c + + 中，預設值是`FALSE`。

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** 啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義。

   Visual c + + 中的執行緒數目是由作業系統決定。

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境變數：這個環境變數的預設值是由實作定義。

   在 Visual c + +、 排程類型是`static`沒有區塊大小。

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境變數：如果未不指定任何值，如`OMP_NUM_THREADS`環境變數，或如果指定的值不是正整數，或如果值大於系統可支援的執行緒數目上限，若要使用的執行緒數目是由實作定義。

   Visual c + + 中，如果未指定值為零，或較少的執行緒數目等於處理器數目。  如果值大於 64，執行緒的數目為 64。

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境變數：預設值是由實作定義。

   Visual c + + 中，預設值是`FALSE`。
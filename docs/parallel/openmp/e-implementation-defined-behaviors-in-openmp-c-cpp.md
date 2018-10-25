---
title: E. 實作定義行為在 OpenMP C/c + + |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c0dd06d5b068c53708f40cb3f8287eac7406255
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055277"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. 實作定義行為在 OpenMP C/c + +

本附錄摘要說明之所以被形容為 「 實作定義 「 此 API 中的行為。  每個行為是交互參考它的主要規格的說明。

## <a name="remarks"></a>備註

的實作都必須定義，並在這些情況下，其行為的文件，但這份清單可能不完整。

- **執行緒的數目：** 如果在平行區域為止已停用動態調整執行緒數目，而要求的平行區域的執行緒數目超出指定的執行階段系統可以提供的行為的數目程式會實作定義 （請參閱第 9 頁）。

   Visual c + + 中，在非巢狀平行區域，64 個執行緒 （最大值） 會提供。

- **處理器數目：** 實際上裝載在任何指定時間的 執行緒的實體處理器的數目是實作定義 （請參閱第 10 頁）。

   Visual c + + 中，這個數字常數，並不由作業系統所控制。

- **建立小組的執行緒：** 小組執行巢狀平行區域的執行緒數目是由實作定義。 (請參閱第 10 頁）。

   在 Visual c + + 中，這取決於作業系統。

- **schedule （runtime):** 有關排程會延遲到執行階段決定。 可以在執行階段選擇的排程類型與區塊大小，藉由設定`OMP_SCHEDULE`環境變數。 如果未設定這個環境變數，產生的排程會實作定義 （請參閱分頁 13）。

   在 Visual c + +、 排程類型是`static`沒有區塊大小。

- **預設排程：** 排程子句如果沒有的預設排程是實作定義 （請參閱分頁 13）。

   在 Visual c + + 中，預設的排程類型是`static`沒有區塊大小。

- **不可部分完成：** 它是由實作定義是否實作會取代所有`atomic`指示詞與**重要**具有相同的唯一名稱 （請參閱頁面 20） 的指示詞。

   Visual c + + 中，如果修改的資料[不可部分完成](../../parallel/openmp/reference/atomic.md)不在自然對齊或如果是 1 或 2 個位元組長時間的所有符合該屬性的不可部分完成作業會使用一個重要區段。 否則，將不會使用重要區段。

- **omp_get_num_threads:** 如果使用者有沒有已明確設定的執行緒數目，預設值是由實作定義 (請參閱第 9 頁並[一節 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 頁上)。

   Visual c + + 中，預設的執行緒數目等於處理器數目。

- **omp_set_dynamic:** 動態執行緒調整的預設值是由實作定義 (請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)上 39)。

   Visual c + + 中，預設值是`FALSE`。

- **omp_set_nested:** 啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義 (請參閱 <<c2> [ 一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上)。

   Visual c + + 中的執行緒數目是由作業系統決定。

- `OMP_SCHEDULE` 環境變數： 這個環境變數的預設值是由實作定義 (請參閱[第 4.1 節](../../parallel/openmp/4-1-omp-schedule.md)上 48 頁)。

   在 Visual c + +、 排程類型是`static`沒有區塊大小。

- `OMP_NUM_THREADS` 環境變數： 如果未不指定任何值，如`OMP_NUM_THREADS`環境變數，或如果指定的值不是正整數，或是如果值大於系統可支援的執行緒數目上限，要使用的執行緒數目實作定義 (請參閱[一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md)上 48 頁)。

   Visual c + + 中，如果未指定值為零，或較少的執行緒數目等於處理器數目。  如果值大於 64，執行緒的數目為 64。

- `OMP_DYNAMIC` 環境變數： 預設值是由實作定義 (請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上)。

   Visual c + + 中，預設值是`FALSE`。
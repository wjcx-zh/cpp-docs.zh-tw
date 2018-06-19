---
title: E. 實作定義行為在 OpenMP C/c + + |Microsoft 文件
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
ms.openlocfilehash: 598964ec6a12ac4c357efc04df78bfbe3af798a5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688696"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. 實作定義的行為在 OpenMP C/c + +
本附錄摘要描述為 「 實作定義 」 此 api 的行為。  每個行為是交互參考它的主要規格的說明。  
  
## <a name="remarks"></a>備註  
 實作可用來定義，並在這些情況下，其行為的文件，但是這份清單可能不完整。  
  
-   **執行緒的數目：** 遇到在平行區域時已停用動態調整執行緒數目，而要求的平行區域的執行緒數目超過執行階段系統可以提供的行為的數目程式會實作定義 （請參閱第 9 頁）。  
  
     Visual c + + 中，在非巢狀平行區域，為 64 個執行緒 （最多） 會提供。  
  
-   **處理器數目：** 實際上裝載執行緒在任何指定時間的實體處理器的數目會實作定義 （請參閱第 10 頁）。  
  
     在 Visual c + + 中，這個數字常數，並不由作業系統所控制。  
  
-   **建立小組，執行緒：** 執行巢狀平行區域在小組中的執行緒數目是由實作定義。 (請參閱第 10 頁）。  
  
     在 Visual c + + 中，這是由作業系統決定。  
  
-   **schedule （runtime):** 有關排程延後到執行階段決定。 可以在執行階段選擇排程類型和區塊大小，藉由設定`OMP_SCHEDULE`環境變數。 如果未設定這個環境變數，產生的排程會實作定義 （請參閱分頁 13）。  
  
     在 Visual c + + 中，排程的類型是`static`沒有區塊大小。  
  
-   **預設排程：** 排程子句不存在，預設排程會實作定義 （請參閱分頁 13）。  
  
     在 Visual c + + 中，預設的排程類型是`static`沒有區塊大小。  
  
-   **不可部分完成：** 它是由實作定義是否實作會取代所有`atomic`指示詞與**重大**具有相同的唯一名稱 （請參閱頁面 20） 的指示詞。  
  
     Visual c + + 中，如果資料修改[不可部分完成](../../parallel/openmp/reference/atomic.md)不在自然對齊或如果是 1 或 2 個位元組長的所有不可部分完成作業，滿足該屬性會使用一個關鍵區段。 否則，不會使用關鍵區段。  
  
-   **omp_get_num_threads:** 如果使用者有沒有已明確設定的執行緒數目，預設值是由實作定義 (請參閱 9 頁和[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 37 頁面上)。  
  
     在 Visual c + +，執行緒的預設數目等於處理器數目。  
  
-   **omp_set_dynamic:** 動態執行緒調整的預設值是由實作定義 (請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)在頁面上 39)。  
  
     Visual c + + 中，預設值是`FALSE`。  
  
-   **omp_set_nested:** 啟用巢狀平行處理原則時，用來執行巢狀平行區域的執行緒數目是由實作定義 (請參閱[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上)。  
  
     Visual c + + 的執行緒數目是由作業系統決定。  
  
-   `OMP_SCHEDULE` 環境變數： 這個環境變數的預設值是由實作定義 (請參閱[第 4.1 節](../../parallel/openmp/4-1-omp-schedule.md)在頁面上 48)。  
  
     在 Visual c + + 中，排程的類型是`static`沒有區塊大小。  
  
-   `OMP_NUM_THREADS` 環境變數： 如果未不指定任何值，如`OMP_NUM_THREADS`環境變數，或如果指定的值不是正整數，或如果值大於系統所支援的執行緒數目上限，要使用的執行緒數目實作定義 (請參閱[區段 4.2](../../parallel/openmp/4-2-omp-num-threads.md)在頁面上 48)。  
  
     Visual c + + 中，如果未指定值為零或更少，執行緒的數目等於處理器數目。  如果值大於 64，執行緒數目是 64。  
  
-   `OMP_DYNAMIC` 環境變數： 預設值是由實作定義 (請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上)。  
  
     Visual c + + 中，預設值是`FALSE`。
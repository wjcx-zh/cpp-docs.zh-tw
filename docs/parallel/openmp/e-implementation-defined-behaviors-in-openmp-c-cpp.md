---
title: "E. Implementation-Defined Behaviors in OpenMP C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# E. Implementation-Defined Behaviors in OpenMP C/C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本附錄會彙總就所謂 「 實作環境 」 這個 API 中的行為。  每個行為是交互參照回它的說明主要的規格。  
  
## 備註  
 實作都必須定義並記載在這些情況下，其行為，但這份清單可能不完整。  
  
-   **執行緒的數目:** 而停用動態調整執行緒的數目，並在平行區域要求的執行緒數目超過執行期間系統能提供的數字，將發生在平行區域，如果程式的行為是實作定義 \(請參閱頁面 9\)。  
  
     在 Visual C\+\+ 中，針對非巢狀的平行區域，64 個執行緒 \(最大值\) 將會提供。  
  
-   **處理器數量:** 實際上裝載在任何指定時間的執行緒的實體處理器數目是實作定義 \(請參閱 10 頁\)。  
  
     在 Visual C\+\+ 中，這個數字常數，並不由作業系統所控制。  
  
-   **建立小組的執行緒：** 的小組中執行巢狀的平行區域的執行緒數目是由實作定義。\(請參閱 10 頁\)。  
  
     在 Visual C\+\+ 中，這是由作業系統決定。  
  
-   **schedule\(runtime\):** 相關排程會延後執行階段的決策。  排程類型和區塊大小可以選擇在執行階段藉由設定`OMP_SCHEDULE`環境變數。  如果未設定這個環境變數，則產生的排程是實作定義 \(請參閱 13 頁\)。  
  
     在 Visual C\+\+ 中，排程的型別是`static`與任何的區塊大小。  
  
-   **排程的預設值：** 沒有排程子句時，預設排程是實作定義 \(請參閱 13 頁\)。  
  
     在 Visual C\+\+ 中，預設的排程類型是`static`與任何的區塊大小。  
  
-   **不可部分完成:** 它是由實作環境是否實作會取代所有`atomic`指示詞與**要徑**有同一個唯一的名稱 \(請參閱 20 頁面\) 的指示詞。  
  
     在 Visual C\+\+，如果資料修改[atomic](../../parallel/openmp/reference/atomic.md)不在自然對齊或如果它是 1 或 2 個位元組長所有滿足該屬性的不可部分完成作業會使用一個關鍵區段。  否則，將不會使用關鍵區段。  
  
-   **omp\_get\_num\_threads:** 如果使用者有沒有被明確設定的執行緒數目，預設值是由實作環境 \(請參閱第 9 頁和[區段 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 在 37\] 頁面上\)。  
  
     在 Visual C\+\+ 中，執行緒預設數目等於處理器數目。  
  
-   **omp\_set\_dynamic:** 的動態執行緒調整預設值是由實作環境 \(請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上\)。  
  
     在 Visual C\+\+ 中，預設值是`FALSE`。  
  
-   **omp\_set\_nested:** 啟用巢狀的平行處理原則時，用來執行巢狀的平行區域的執行緒數目是由實作環境 \(請參閱[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 在頁面上 40\)。  
  
     Visual C\+\+ 中，執行緒的數目是由作業系統決定。  
  
-   `OMP_SCHEDULE`環境變數： 這個環境變數的預設值是由實作環境 \(請參閱[一節 4.1](../../parallel/openmp/4-1-omp-schedule.md) 在頁面上 48\)。  
  
     在 Visual C\+\+ 中，排程的型別是`static`與任何的區塊大小。  
  
-   `OMP_NUM_THREADS`環境變數： 如果沒有指定值的`OMP_NUM_THREADS`環境變數，或如果指定的值不是正整數，或如果值大於最大的系統所支援的執行緒數目，若要使用的執行緒數目是由實作環境 \(請參閱[區段 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 在頁面上 48\)。  
  
     在 Visual C\+\+ 中，如果指定值為零或更少，執行緒的數目等於處理器數目。  如果值是大於 64，執行緒的數目為 64。  
  
-   `OMP_DYNAMIC`環境變數： 預設值是由實作環境 \(請參閱 [4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)在 49\] 頁面上\)。  
  
     在 Visual C\+\+ 中，預設值是`FALSE`。
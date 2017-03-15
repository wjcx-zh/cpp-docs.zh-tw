---
title: "2.3 parallel Construct | Microsoft Docs"
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
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.3 parallel Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列指示詞會定義在平行區域，是由多個執行緒同時執行該程式的區域。  這是基本的架構開始平行執行。  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line  
   structured-block  
```  
  
 *子句*是下列其中一項：  
  
 **如果 \(** *純量運算式* **\)**  
  
 **私用 \(** *變數清單* **\)**  
  
 **firstprivate \(** *變數清單* **\)**  
  
 **default\(shared &#124; none\)**  
  
 **共用 \(** *變數清單* **\)**  
  
 **copyin \(** *變數清單* **\)**  
  
 **reduction\(** *operator* **:**  *variable\-list* **\)**  
  
 **num\_threads \(** *整數運算式* **\)**  
  
 當執行緒遇到平行建構時，其中一個下列的情況下，則為 true 時，會建立一群執行緒：  
  
-   不**如果**子句會出現。  
  
-   **如果**的運算式評估為非零的值。  
  
 此執行緒就會變成主執行緒的小組成員，以執行緒數字為 0，和小組成員，包括主要的執行緒中的所有執行緒平行地都執行區域。  如果值為**如果**運算式為零、 序列化 \(地區\)。  
  
 如果要判斷所要求的執行緒數目，下列規則會被視為順序。  第一個符合條件的規則將套用：  
  
1.  如果 **num\_threads** 子句是存在，那麼整數運算式的值就是要求的執行緒數目。  
  
2.  如果 **omp\_set\_num\_threads** 程式庫函式被呼叫，那麼最近執行的呼叫中的引數的值就是要求的執行緒數目。  
  
3.  如果環境變數 **OMP\_NUM\_THREADS** 定義，那麼這個環境變數的值就是要求的執行緒數目。  
  
4.  如果使用上述的方法，然後要求的執行緒數目是由實作定義。  
  
 如果 **num\_threads** 子句存在就取代了所要求的執行緒數目代表 **omp\_set\_num\_threads** 程式庫函式或 **OMP\_NUM\_THREADS** 只用於平行區域，它會套用到環境變數。  後續的平行區域不會影響它。  
  
 執行平行區域的執行緒數目也會根據是否不信由您啟用動態調整執行緒的數目。  如果停用動態調整時，所要求的執行緒數目會執行平行區域。  如果已啟用動態調整所要求的執行緒數目則可能會一直執行平行區域的執行緒的最大數目。  
  
 如果在平行區域時發生的數字的動態調整執行緒已停用，並在平行區域要求的執行緒數目超過執行期間系統能提供的數字，程式的行為是由實作環境。  實作可能會，比方說，中斷執行的程式，或者它可以將平行區域進行序列化。  
  
 **Omp\_set\_dynamic** 程式庫函式和 **OMP\_DYNAMIC** 環境變數可用來啟用及停用動態調整執行緒的數目。  
  
 實際上裝載在任何指定時間的執行緒的實體處理器數目是由實作定義。  保持一旦建立之後，小組中的執行緒數目不變的平行區域的持續期間。  可能是由使用者明確地或自動執行階段系統從一個平行區域到另一個可以變更它。  
  
 包含在平行區域的動態範圍內的陳述式執行的每個執行緒，而且每個執行緒可以執行陳述式的不同於其他執行緒的路徑。  發生在平行區域的語彙範圍外的指示詞被指被遺棄的指示詞。  
  
 沒有暗示的障盾在平行區域結尾處。  小組的主要執行緒會繼續在平行區域結尾處的執行。  
  
 如果小組，執行在平行區域中的執行緒遇到另一個平行建構，它會建立新的小組，，並成為該新的小組的母片。  預設情況下，巢狀的平行區域都會加以序列化。  如此一來，預設情況下，巢狀的平行區域是由一個執行緒所組成的小組執行。  預設的行為可能會變更使用執行階段程式庫函數 **omp\_set\_nested** 或環境變數 **OMP\_NESTED**。  不過，小組中執行巢狀的平行區域的執行緒數目是由實作定義。  
  
 若要限制**平行**指示詞如下：  
  
-   最多一個**如果**子句可以出現在指示詞。  
  
-   這是未指定任何側邊的效果置於 if 運算式或 **num\_threads** 運算式就會發生。  
  
-   A **擲回**執行在平行區域必須誘使才能繼續在相同的結構化區塊中，動態範圍內執行，而且必須由相同執行緒擲回例外狀況發生了。  
  
-   只會有一個 **num\_threads** 子句可以出現在指示詞。  **Num\_threads** 運算式評估內容以外的平行區域中，並且都必評估為正整數值。  
  
-   評估的順序**如果**和  **num\_threads** 未指定子句。  
  
## 交互參照：  
  
-   **私用**，  **firstprivate**， **預設**， **共用**，  **copyin**，以及 **降低**子句，請參閱 [區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 在 25\] 頁面上。  
  
-   **OMP\_NUM\_THREADS** 環境變數， [一節 4.2](../../parallel/openmp/4-2-omp-num-threads.md) 在 48\] 頁面上。  
  
-   **omp\_set\_dynamic** 程式庫函式，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。  
  
-   **OMP\_DYNAMIC** 環境變數，請參閱 [4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)在 49\] 頁面上。  
  
-   **omp\_set\_nested** 函式，請參閱[一節 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 在 40\] 頁面上。  
  
-   **OMP\_NESTED** 環境變數，請參閱 [4.4 節](../../parallel/openmp/4-4-omp-nested.md)在 49\] 頁面上。  
  
-   **omp\_set\_num\_threads** 程式庫函式，請參閱[一節 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 在 36\] 頁面上。
---
title: "Concurrency 命名空間 (C++ AMP) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Concurrency 命名空間"
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency 命名空間 (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供類別和資料平行硬體加速的 c + + 程式碼執行的函式。 如需詳細資訊，請參閱 [c + + AMP 概觀](../../../parallel/amp/cpp-amp-overview.md)  
  
## <a name="syntax"></a>語法  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Members  
  
### <a name="namespaces"></a>命名空間  
  
|名稱|描述|  
|----------|-----------------|  
|[Concurrency:: direct3d 命名空間](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)|提供支援 D3D 互通性的函式。 可讓順暢地將 D3D 資源 AMP 程式碼中的計算並且使用所建立的資源 AMP D3D 程式碼中，而不需建立中繼副本。 您可以使用 c + + AMP 累加加速運算密集的部份 DirectX 應用程式，並使用 D3D API AMP 計算所產生的資料。|  
|[Concurrency:: fast_math 命名空間](../../../parallel/amp/reference/concurrency-fast-math-namespace.md)|函式的 `fast_math` 命名空間不符合 C99 標準。 只有每個函式的單精確度版本都會提供。 這些函式會使用 DirectX 內建函式，也就是比對應的函式中 `precise_math` 命名空間並不需要擴充的雙精確度支援加速器上，但它們是較不精確。 有兩個版本的來源層級相容性的 C99 程式碼; 每個函式這兩個版本使用，並傳回單精確度值。|  
|[Concurrency:: graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)|圖形程式設計提供型別和函式所設計。|  
|[Concurrency:: precise_math 命名空間](../../../parallel/amp/reference/concurrency-precise-math-namespace.md)|函式的 `precise_math` 命名空間是 C99 標準。 每個函式的單精確度和雙精度版本隨附。 這些函式，包括單精確度函式 — 需要擴充的雙精確度支援加速器上。|  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[accelerator 類別](../../../parallel/amp/reference/accelerator-class.md)|表示實體 DP 最佳化的運算節點的抽象概念。|  
|[accelerator_view 類別](../../../parallel/amp/reference/accelerator-view-class.md)|表示在 c + + AMP 資料平行加速器上的虛擬裝置抽象概念。|  
|[accelerator_view_removed 類別](../../../parallel/amp/reference/accelerator-view-removed-class.md)|由於 Windows 逾時-偵測-和-復原機制的基礎的 DirectX 呼叫失敗時擲回例外狀況。|  
|[array 類別](../../../parallel/amp/reference/array-class.md)|將資料彙總上 `accelerator_view` 方格網域中。 它是每個項目方格網域中的變數集合。 每個變數會保留其值為 c + + 型別對應。|  
|[array_view 類別](../../../parallel/amp/reference/array-view-class.md)|表示陣列 \< T、 N > 中資料的檢視。|  
|[completion_future 類別](../../../parallel/amp/reference/completion-future-class.md)|代表對應未來 c + + AMP 的非同步作業。|  
|[extent 類別](../../../parallel/amp/reference/extent-class-cpp-amp.md)|表示 N 指定具有 0 原點的 N 維空間的範圍的整數值的向量。 座標的向量中的值為從最大顯著性到最小顯著性排序。 比方說，在笛卡兒 3d 空間中，範圍向量 (7,5,3) 代表的空間，其中的 z 座標範圍從 0 到 7，y 座標範圍從 0 到 5，而且的 x 座標，範圍從 0 到 3。|  
|[index 類別](../../../parallel/amp/reference/index-class.md)|定義 N 維索引點。|  
|[invalid_compute_domain 類別](../../../parallel/amp/reference/invalid-compute-domain-class.md)|執行階段無法啟動一個核心使用在指定的運算網域時，會擲回的例外狀況 `parallel_for_each` 呼叫站台。|  
|[out_of_memory 類別](../../../parallel/amp/reference/out-of-memory-class.md)|由於系統或裝置的記憶體不足的方法失敗時擲回的例外狀況。|  
|[runtime_exception 類別](../../../parallel/amp/reference/runtime-exception-class.md)|C + + AMP 程式庫中的例外狀況的基底類型。|  
|[tile_barrier 類別](../../../parallel/amp/reference/tile-barrier-class.md)|功能類別，才可由系統建立並傳遞至並排 `parallel_for_each` 一部分 lambda `tiled_index` 參數。 它提供一種方法， `wait()`, ，其目的是要同步處理的執行緒群組 （並排顯示） 中執行的執行緒執行。|  
|[tiled_extent 類別](../../../parallel/amp/reference/tiled-extent-class.md)|A `tiled_extent` 物件是 `extent` 細分成一維、 二維或立體範圍空間一到三個維度的物件。|  
|[tiled_index 類別](../../../parallel/amp/reference/tiled-index-class.md)|提供的索引 `tiled_grid` 物件。 這個類別包含屬性來存取項目相對於本機磚原點和相對於全域來源。|  
|[uninitialized_object 類別](../../../parallel/amp/reference/uninitialized-object-class.md)|使用未初始化的物件時，會擲回例外狀況。|  
|[unsupported_feature 類別](../../../parallel/amp/reference/unsupported-feature-class.md)|使用不支援的功能時，會擲回例外狀況。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|描述|  
|----------|-----------------|  
|[access_type 列舉](../Topic/access_type%20Enumeration.md)|指定資料的存取類型。|  
|[queuing_mode 列舉](../../../parallel/amp/reference/queuing-mode-enumeration.md)|指定的佇列模式所支援的快速鍵。|  
  
### <a name="operators"></a>運算子  
  
|運算子|描述|  
|--------------|-----------------|  
|[運算子 = = 運算子 (c + + AMP)](../Topic/operator==%20Operator%20\(C++%20AMP\).md)|判斷指定的資料結構是否相等。|  
|[運算子 ！ = 運算子 (c + + AMP)](../Topic/operator!=%20Operator%20\(C++%20AMP\).md)|判斷指定的資料結構是否不相等。|  
|[operator + 運算子 (c + + AMP)](../Topic/operator+%20Operator%20\(C++%20AMP\).md)|計算 component-wise 指定的引數的總和。|  
|[operator-運算子 (c + + AMP)](../Topic/operator-%20Operator%20\(C++%20AMP\)1.md)|計算指定的引數的 component-wise 差異。|  
|[運算子 * 運算子 (c + + AMP)](../Topic/operator*%20Operator%20\(C++%20AMP\).md)|計算指定的引數的 component-wise 的乘積。|  
|[運算子 / 運算子 (c + + AMP)](../Topic/operator-%20Operator%20\(C++%20AMP\)2.md)|計算指定的引數的 component-wise 的商數。|  
|[operator %運算子 (c + + AMP)](../Topic/operator%25%20Operator%20\(C++%20AMP\).md)|計算的第一個指定的引數，第二個指定的引數的模數。|  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[all_memory_fence 函式](../Topic/all_memory_fence%20Function.md)|區塊執行的所有執行緒，直到完成為止的所有記憶體存取在磚中。|  
|[amp_uninitialize 函式](../Topic/amp_uninitialize%20Function.md)|未初始化 c + + AMP 執行階段。|  
|[atomic_compare_exchange 函式](../Topic/atomic_compare_exchange%20Function.md)|多載。 儲存指定之位置的值等於第一個指定的值，如果第二個指定的值儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_exchange 函式](../Topic/atomic_exchange%20Function%20\(C++%20AMP\).md)|多載。 設定儲存在指定的值成為不可部分完成的作業指定的位置的值。|  
|[atomic_fetch_add 函式](../Topic/atomic_fetch_add%20Function%20\(C++%20AMP\).md)|多載。 設定儲存為該值與指定之的值的總和，成為不可部分完成的作業指定位置的值。|  
|[atomic_fetch_and 函式](../Topic/atomic_fetch_and%20Function%20\(C++%20AMP\).md)|多載。 設定儲存在指定的位置，以位元的值 `and` 該值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_dec 函式](../Topic/atomic_fetch_dec%20Function.md)|多載。 遞減值儲存在指定的位置，並將結果儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_fetch_inc 函式](../Topic/atomic_fetch_inc%20Function.md)|多載。 遞增儲存在指定位置的值，並將結果儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_fetch_max 函式](../Topic/atomic_fetch_max%20Function.md)|多載。 設定儲存在指定的位置，以較大的值的值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_min 函式](../Topic/atomic_fetch_min%20Function.md)|多載。 設定儲存在指定的位置，以較小的值的值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_or 函式](../Topic/atomic_fetch_or%20Function%20\(C++%20AMP\).md)|多載。 設定儲存在指定的位置，以位元的值 `or` 該值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_sub 函式](../Topic/atomic_fetch_sub%20Function%20\(C++%20AMP\).md)|多載。 設定儲存到該值與指定的值的差異，成為不可部分完成的作業的指定位置的值。|  
|[atomic_fetch_xor 函式](../Topic/atomic_fetch_xor%20Function%20\(C++%20AMP\).md)|多載。 設定儲存在指定的位置，以位元的值 `xor` 該值和指定的值，成為不可部分完成的作業。|  
|[copy 函式](../Topic/copy%20Function.md)|將 c + + AMP 物件複製。 符合所有同步的資料傳輸需求。 快速鍵的程式碼執行的程式碼時，無法複製資料。 此函式的一般形式是 `copy(src, dest)`。|  
|[copy_async 函式](../Topic/copy_async%20Function.md)|複製 c + + AMP 物件並傳回 [completion_future](../../../parallel/amp/reference/completion-future-class.md) 可以等候的。 加速器上執行的程式碼時，無法複製資料。 此函式的一般形式是 `copy(src, dest)`。|  
|[direct3d_abort 函式](../Topic/direct3d_abort%20Function.md)|中止執行函式具有 `restrict(amp)` 限制子句。|  
|[direct3d_errorf 函式](../Topic/direct3d_errorf%20Function.md)|列印到 Visual Studio 的格式化的字串 **輸出** 視窗並引發 [runtime_exception](../../../parallel/amp/reference/runtime-exception-class.md) 格式設定相同的例外狀況的字串。|  
|[direct3d_printf 函式](../Topic/direct3d_printf%20Function.md)|列印到 Visual Studio 的格式化的字串 **輸出** 視窗。 從擁有的函式呼叫 `restrict(amp)` 限制子句。|  
|[global_memory_fence 函式](../Topic/global_memory_fence%20Function.md)|已完成的所有執行緒，直到所有的全域記憶體存取在磚中的區塊執行。|  
|[parallel_for_each 函式 (c + + AMP)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)|在計算網域中執行的函式。|  
|[tile_static_memory_fence 函式](../Topic/tile_static_memory_fence%20Function.md)|封鎖直到磚中的所有執行緒的執行 `tile_static` 已完成的記憶體存取。|  
  
## <a name="constants"></a>常數  
  
|名稱|描述|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS 常數](../Topic/HLSL_MAX_NUM_BUFFERS%20Constant.md)|DirectX 所允許的緩衝區最大數目。|  
|[MODULENAME_MAX_LENGTH 常數](../Topic/MODULENAME_MAX_LENGTH%20Constant.md)|將模組名稱的最大長度。 此值必須是相同的編譯器和執行階段。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
## <a name="see-also"></a>請參閱  
 [參考 (c + + AMP)](../../../parallel/amp/reference/reference-cpp-amp.md)




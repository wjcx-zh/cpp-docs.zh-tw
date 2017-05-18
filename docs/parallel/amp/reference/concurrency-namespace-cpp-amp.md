---
title: "Concurrency 命名空間 (c + + AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 38c3154244b163202bcb8e271f96b393231247ca
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空間 (C++ AMP)
提供類別和資料平行硬體加速的 c + + 程式碼執行的函式。 如需詳細資訊，請參閱[c + + AMP 概觀](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>語法  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Members  
  
### <a name="namespaces"></a>命名空間  
  
|名稱|描述|  
|----------|-----------------|  
|[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)|提供支援 D3D 互通性的函式。 可讓順暢地將 D3D 資源 AMP 程式碼中的計算並且使用所建立的資源 AMP D3D 程式碼中，而不需建立中繼副本。 您可以使用 c + + AMP 累加加速運算密集的部份 DirectX 應用程式，並使用 D3D API AMP 計算所產生的資料。|  
|[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)|函式的`fast_math`命名空間不符合 C99 標準。 只有每個函式的單精確度版本都會提供。 這些函式會使用 DirectX 內建函式，也就是比對應的函式中`precise_math`命名空間並不需要擴充的雙精確度支援加速器上，但它們是較不精確。 有兩個版本的來源層級相容性的 C99 程式碼; 每個函式這兩個版本使用，並傳回單精確度值。|  
|[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)|圖形程式設計提供型別和函式所設計。|  
|[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)|函式的`precise_math`命名空間是 C99 標準。 每個函式的單精確度和雙精度版本隨附。 這些函式，包括單精確度函式 — 需要擴充的雙精確度支援加速器上。|  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[accelerator 類別](accelerator-class.md)|表示實體 DP 最佳化的運算節點的抽象概念。|  
|[accelerator_view 類別](accelerator-view-class.md)|表示在 c + + AMP 資料平行加速器上的虛擬裝置抽象概念。|  
|[accelerator_view_removed 類別](accelerator-view-removed-class.md)|由於 Windows 逾時-偵測-和-復原機制的基礎的 DirectX 呼叫失敗時擲回例外狀況。|  
|[array 類別](array-class.md)|將資料彙總上`accelerator_view`方格網域中。 它是每個項目方格網域中的變數集合。 每個變數會保留其值為 c + + 型別對應。|  
|[array_view 類別](array-view-class.md)|表示陣列中資料的檢視\<T、 N >。|  
|[completion_future 類別](completion-future-class.md)|代表對應未來 c + + AMP 的非同步作業。|  
|[extent 類別](extent-class.md)|表示 N 指定具有 0 原點的 N 維空間的範圍的整數值的向量。 座標的向量中的值為從最大顯著性到最小顯著性排序。 比方說，在笛卡兒 3d 空間中，範圍向量 (7,5,3) 代表的空間，其中的 z 座標範圍從 0 到 7，y 座標範圍從 0 到 5，而且的 x 座標，範圍從 0 到 3。|  
|[index 類別](index-class.md)|定義 N 維索引點。|  
|[invalid_compute_domain 類別](invalid-compute-domain-class.md)|執行階段無法啟動一個核心使用在指定的運算網域時，會擲回的例外狀況`parallel_for_each`呼叫站台。|  
|[out_of_memory 類別](out-of-memory-class.md)|由於系統或裝置的記憶體不足的方法失敗時擲回的例外狀況。|  
|[runtime_exception 類別](runtime-exception-class.md)|C + + AMP 程式庫中的例外狀況的基底類型。|  
|[tile_barrier 類別](tile-barrier-class.md)|功能類別，才可由系統建立並傳遞至並排`parallel_for_each`一部分 lambda`tiled_index`參數。 它提供一種方法， `wait()`，其目的是要同步處理的執行緒群組 （並排顯示） 中執行的執行緒執行。|  
|[tiled_extent 類別](tiled-extent-class.md)|A`tiled_extent`物件是`extent`細分成一維、 二維或立體範圍空間一到三個維度的物件。|  
|[tiled_index 類別](tiled-index-class.md)|提供的索引`tiled_grid`物件。 這個類別包含屬性來存取項目相對於本機磚原點和相對於全域來源。|  
|[uninitialized_object 類別](uninitialized-object-class.md)|使用未初始化的物件時，會擲回例外狀況。|  
|[unsupported_feature 類別](unsupported-feature-class.md)|使用不支援的功能時，會擲回例外狀況。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|描述|  
|----------|-----------------|  
|[access_type 列舉](concurrency-namespace-enums-amp.md#access_type)|指定資料的存取類型。|  
|[queuing_mode 列舉](concurrency-namespace-enums-amp.md#queuing_mode)|指定的佇列模式所支援的快速鍵。|  
  
### <a name="operators"></a>運算子  
  
|運算子|描述|  
|--------------|-----------------|  
|[運算子 = = 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|判斷指定的資料結構是否相等。|  
|[運算子 ！ = 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_neq)|判斷指定的資料結構是否不相等。|  
|[operator + 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_add)|計算 component-wise 指定的引數的總和。|  
|[operator-運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator-)|計算指定的引數的 component-wise 差異。|  
|[運算子 * 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_star)|計算指定的引數的 component-wise 的乘積。|  
|[運算子 / 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_div)|計算指定的引數的 component-wise 的商數。|  
|[operator %運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_mod)|計算的第一個指定的引數，第二個指定的引數的模數。|  
  
### <a name="functions"></a>函式  
  
|名稱|說明|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|區塊執行的所有執行緒，直到完成為止的所有記憶體存取在磚中。|  
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|未初始化 c + + AMP 執行階段。|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|多載。 儲存指定之位置的值等於第一個指定的值，如果第二個指定的值儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|多載。 設定儲存在指定的值成為不可部分完成的作業指定的位置的值。|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|多載。 設定儲存為該值與指定之的值的總和，成為不可部分完成的作業指定位置的值。|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|多載。 設定儲存在指定的位置，以位元的值`and`該值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|多載。 遞減值儲存在指定的位置，並將結果儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|多載。 遞增儲存在指定位置的值，並將結果儲存在相同的位置，成為不可部分完成的作業。|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|多載。 設定儲存在指定的位置，以較大的值的值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|多載。 設定儲存在指定的位置，以較小的值的值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|多載。 設定儲存在指定的位置，以位元的值`or`該值和指定的值，成為不可部分完成的作業。|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|多載。 設定儲存到該值與指定的值的差異，成為不可部分完成的作業的指定位置的值。|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|多載。 設定儲存在指定的位置，以位元的值`xor`該值和指定的值，成為不可部分完成的作業。|  
|[copy](concurrency-namespace-functions-amp.md#copy)|將 c + + AMP 物件複製。 符合所有同步的資料傳輸需求。 快速鍵的程式碼執行的程式碼時，無法複製資料。 此函式的一般形式是`copy(src, dest)`。|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|複製 c + + AMP 物件並傳回[completion_future](completion-future-class.md)可以等候的。 加速器上執行的程式碼時，無法複製資料。 此函式的一般形式是`copy(src, dest)`。|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止執行函式具有`restrict(amp)`限制子句。|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|列印到 Visual Studio 的格式化的字串**輸出**視窗並引發[runtime_exception](runtime-exception-class.md)格式設定相同的例外狀況的字串。|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|列印到 Visual Studio 的格式化的字串**輸出**視窗。 從擁有的函式呼叫`restrict(amp)`限制子句。|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|已完成的所有執行緒，直到所有的全域記憶體存取在磚中的區塊執行。|  
|[parallel_for_each 函式 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|在計算網域中執行的函式。|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|封鎖直到磚中的所有執行緒的執行`tile_static`已完成的記憶體存取。|  
  
## <a name="constants"></a>常數  
  
|名稱|說明|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS 常數](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX 所允許的緩衝區最大數目。|  
|[MODULENAME_MAX_LENGTH 常數](concurrency-namespace-constants-amp.md#modulename_max_length)|將模組名稱的最大長度。 此值必須是相同的編譯器和執行階段。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
## <a name="see-also"></a>另請參閱  
 [參考 (C++ AMP)](reference-cpp-amp.md)





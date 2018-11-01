---
title: Concurrency 命名空間 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 5ddafe5dd821fb21eb6dd03d63122fa98a56af51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635366"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空間 (C++ AMP)

提供類別和資料平行硬體加速的 c + + 程式碼執行的函式。 如需詳細資訊，請參閱[c + + AMP 概觀](../cpp-amp-overview.md)

## <a name="syntax"></a>語法

```
namespace Concurrency;
```

## <a name="members"></a>成員

### <a name="namespaces"></a>命名空間

|名稱|描述|
|----------|-----------------|
|[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)|提供支援 D3D 互通性的函式。 能夠充分運用 D3D 資源在 AMP 程式碼中的計算以及使用的資源在 AMP 中 D3D 程式碼建立，而不需要建立中繼複本。 您可以使用 c + + AMP，以累加方式加速 DirectX 應用程式的大量運算區段和 D3D 介面用於 AMP 計算所產生的資料。|
|[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)|中的函式`fast_math`命名空間不符合 C99 標準。 只有每個函式的單精確度版本提供。 這些函式使用 DirectX 內建函式，也就是較快，對應的函式中`precise_math`命名空間並不需要擴充的雙精確度支援快速鍵，但較不精確。 有兩個版本的來源層級與 C99 程式碼; 的相容性的每個函式這兩個版本會接受並傳回單精確度值。|
|[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)|提供型別和函式專為圖形程式設計。|
|[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)|中的函式`precise_math`命名空間會符合 C99 標準。 每個函式的單精確度和雙精確度版本會包含項目。 這些函式 — 包括單精確度函式，需要在加速器上的擴充的雙精確度支援。|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[accelerator 類別](accelerator-class.md)|代表實體 DP 最佳化運算節點的抽象概念。|
|[accelerator_view 類別](accelerator-view-class.md)|表示在 c + + AMP 資料平行加速器上的虛擬裝置抽象概念。|
|[accelerator_view_removed 類別](accelerator-view-removed-class.md)|因為 Windows 逾時偵測-和復原機制的基礎 DirectX 呼叫失敗時擲回的例外狀況。|
|[array 類別](array-class.md)|將資料彙總上`accelerator_view`方格網域中。 它是變數，每個項目，對應方格網域中的集合。 每個變數會保留對應某個 c + + 類型的值。|
|[array_view 類別](array-view-class.md)|表示陣列中資料的檢視\<T，N> >。|
|[completion_future 類別](completion-future-class.md)|表示對應的未來，c + + AMP 非同步處理操作。|
|[extent 類別](extent-class.md)|表示 N 指定為 0 為原點的 N 維空間的範圍的整數值的向量。 在座標向量中的值排序從最大顯著性到最不重要。 比方說，在笛卡兒 3 維空間中，範圍向量 (7,5,3) 表示的空間中的 z 座標範圍從 0 到 7，y 座標範圍從 0 變更為 5，和的 x 座標範圍從 0 到 3。|
|[index 類別](index-class.md)|定義 N 維索引點。|
|[invalid_compute_domain 類別](invalid-compute-domain-class.md)|執行階段無法使用在指定的計算網域啟動核心時，會擲回的例外狀況`parallel_for_each`呼叫站台。|
|[out_of_memory 類別](out-of-memory-class.md)|方法失敗，因為系統或裝置的記憶體不足時，會擲回例外狀況。|
|[runtime_exception 類別](runtime-exception-class.md)|C + + AMP 文件庫中的例外狀況的基底型別。|
|[tile_barrier 類別](tile-barrier-class.md)|功能類別只是由系統建立，並傳遞至並排`parallel_for_each`一部分的 lambda`tiled_index`參數。 它提供一種方法， `wait()`，其目的是要同步處理在執行緒群組 (tile) 中執行的執行緒的執行。|
|[tiled_extent 類別](tiled-extent-class.md)|A`tiled_extent`物件是`extent`將範圍空間到一維、 二維或三維的拼貼一到三個維度的物件。|
|[tiled_index 類別](tiled-index-class.md)|提供索引`tiled_grid`物件。 這個類別具有存取相對於本機磚原點和相對於全域原點的項目屬性。|
|[uninitialized_object 類別](uninitialized-object-class.md)|使用未初始化的物件時擲回的例外狀況。|
|[unsupported_feature 類別](unsupported-feature-class.md)|使用不支援的功能時，會擲回例外狀況。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[access_type 列舉](concurrency-namespace-enums-amp.md#access_type)|指定資料的存取類型。|
|[queuing_mode 列舉](concurrency-namespace-enums-amp.md#queuing_mode)|指定在加速器支援的佇列模式。|

### <a name="operators"></a>運算子

|運算子|描述|
|--------------|-----------------|
|[運算子 = = 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|判斷指定的資料結構是否相等。|
|[運算子 ！ = 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_neq)|判斷指定的資料結構是否不相等。|
|[operator + 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_add)|計算指定的引數的整體元件總和。|
|[operator-運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator-)|計算指定的引數之間的整體元件差值。|
|[運算子 * 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_star)|計算指定的引數的整體元件乘積。|
|[運算子 / 運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_div)|計算指定的引數的整體元件商數。|
|[operator %運算子 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_mod)|計算的第一個指定的引數，第二個指定的引數的模數。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|所有的執行緒，直到所有記憶體存取都已經都完成的區塊執行。|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消初始化 c + + AMP 執行階段。|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|多載。 儲存在指定位置的值比較為相等的第一個指定的值，如果第二個指定的值是會儲存在相同的位置，成為不可部分完成的作業。|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|多載。 設定儲存在指定的值做為不可部分完成的作業指定的位置的值。|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|多載。 設定儲存在不可部分完成的作業為該值與所指定的值的總和指定位置的值。|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|多載。 設定儲存在指定位置的位元值`and`的該值與指定的值，成為不可部分完成的作業。|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|多載。 遞減值儲存在指定的位置，並將結果儲存在不可部分完成的作業相同的位置。|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|多載。 遞增的值儲存在指定的位置，並將結果儲存在不可部分完成的作業相同的位置。|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|多載。 設定儲存在指定的位置，以較大的值的值與所指定的值，成為不可部分完成的作業。|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|多載。 設定儲存在指定的位置，以較小的值的值與所指定的值，成為不可部分完成的作業。|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|多載。 設定儲存在指定位置的位元值`or`的該值與指定的值，成為不可部分完成的作業。|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|多載。 設定儲存在指定的位置，該值與所指定的值的差異，以不可部分完成作業的值。|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|多載。 設定儲存在指定位置的位元值`xor`的該值與指定的值，成為不可部分完成的作業。|
|[copy](concurrency-namespace-functions-amp.md#copy)|複製 c + + AMP 物件。 已符合所有的同步資料傳輸需求。 程式碼會在加速器上執行的程式碼時，無法複製資料。 此函式的一般形式是`copy(src, dest)`。|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|複製 c + + AMP 物件並傳回[completion_future](completion-future-class.md)可以等候。 當在加速器上執行的程式碼時，無法複製資料。 此函式的一般形式是`copy(src, dest)`。|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止的函式執行`restrict(amp)`限制子句。|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|列印格式化的字串，Visual studio**輸出**視窗，並引發[runtime_exception](runtime-exception-class.md)具有相同格式的例外狀況的字串。|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|列印格式化的字串，Visual studio**輸出**視窗。 呼叫的函式從`restrict(amp)`限制子句。|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|封鎖直到所有全域記憶體存取的所有執行緒的執行已完成。|
|[parallel_for_each 函式 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|整個計算網域中執行的函式。|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|封鎖直到磚中的所有執行緒的執行`tile_static`記憶體存取都已經完成。|

## <a name="constants"></a>常數

|名稱|描述|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 常數](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX 允許的緩衝區最大數目。|
|[MODULENAME_MAX_LENGTH 常數](concurrency-namespace-constants-amp.md#modulename_max_length)|儲存模組名稱的最大長度。 此值必須是相同的編譯器和執行階段。|

## <a name="requirements"></a>需求

**標頭︰** amp.h

## <a name="see-also"></a>另請參閱

[參考 (C++ AMP)](reference-cpp-amp.md)


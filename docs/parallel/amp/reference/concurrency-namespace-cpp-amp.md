---
title: Concurrency 命名空間 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139364"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空間 (C++ AMP)

提供可加速在資料平行硬體上執行C++程式碼的類別和函式。 如需詳細資訊，請參閱[ C++ AMP 總覽](../cpp-amp-overview.md)

## <a name="syntax"></a>語法

```cpp
namespace Concurrency;
```

## <a name="members"></a>成員

### <a name="namespaces"></a>命名空間

|名稱|描述|
|----------|-----------------|
|[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)|提供支援 D3D 互通性的功能。 針對 AMP 程式碼中的計算，以及使用在 D3D 程式碼中建立的資源，無需建立多餘的中繼複本，即可順暢地使用 D3D 資源。 您可以使用C++ amp 以累加方式加速 DirectX 應用程式的計算密集型區段，並針對 AMP 計算所產生的資料使用 D3D API。|
|[Concurrency::fast_math 命名空間](concurrency-fast-math-namespace.md)|`fast_math` 命名空間中的函數不符合 C99 規範。 只提供每個函數的單精確度版本。 這些函式使用 DirectX 內建函式，其速度比 `precise_math` 命名空間中的對應函式還快，而且不需要加速器的擴充雙精確度支援，但較不精確。 每個函式都有兩個版本，以便與 C99 程式碼進行來源層級相容性;這兩個版本都採用並傳回單精確度值。|
|[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)|提供的類型和函式是針對圖形程式設計所設計。|
|[Concurrency::precise_math 命名空間](concurrency-precise-math-namespace.md)|`precise_math` 命名空間中的函式符合 C99 規範。 其中包含每個函式的單精確度和雙精確度版本。 這些函式（包括單精確度函數）在加速器上需要擴充的雙精確度支援。|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[accelerator 類別](accelerator-class.md)|表示實體 DP 優化計算節點的抽象概念。|
|[accelerator_view 類別](accelerator-view-class.md)|代表C++ AMP 資料平行加速器上的虛擬裝置抽象化。|
|[accelerator_view_removed 類別](accelerator-view-removed-class.md)|當基礎 DirectX 呼叫因 Windows 超時偵測和修復機制而失敗時，所擲回的例外狀況。|
|[array 類別](array-class.md)|方格定義域中 `accelerator_view` 的資料匯總。 它是變數的集合，格線定義域中的每個元素各一個。 每個變數都會保存一個對應至某個C++類型的值。|
|[array_view 類別](array-view-class.md)|代表陣列中資料的視圖，\<T，N >。|
|[completion_future 類別](completion-future-class.md)|表示對應于C++ AMP 非同步作業的未來。|
|[extent 類別](extent-class.md)|代表 N 個整數值的向量，指定具有原點為0之 N 維度空間的範圍。 座標向量中的值會從最重要到最低的順序排序。 例如，在笛卡兒3維空間中，範圍向量（7，5，3）表示 z 座標的範圍是從0到7，而 y 座標的範圍是從0到5，而 x 座標的範圍是從0到3。|
|[index 類別](index-class.md)|定義 N 維索引點。|
|[invalid_compute_domain 類別](invalid-compute-domain-class.md)|當執行時間無法使用在 `parallel_for_each` 呼叫位置指定的計算網域來啟動核心時，所擲回的例外狀況。|
|[out_of_memory 類別](out-of-memory-class.md)|當方法因為缺乏系統或裝置記憶體而失敗時，所擲回的例外狀況。|
|[runtime_exception 類別](runtime-exception-class.md)|C++ AMP 程式庫中的例外狀況基底類型。|
|[tile_barrier 類別](tile-barrier-class.md)|只能由系統建立的功能類別，而且會傳遞至磚 `parallel_for_each` lambda 做為 `tiled_index` 參數的一部分。 它提供一個方法，`wait()`，其目的是要同步處理執行緒群組（磚）中執行的執行緒。|
|[tiled_extent 類別](tiled-extent-class.md)|`tiled_extent` 物件是一到三個維度的 `extent` 物件，可將範圍空間會細分為一維、二維或三維磚。|
|[tiled_index 類別](tiled-index-class.md)|提供 `tiled_grid` 物件的索引。 這個類別具有屬性，可存取相對於本機磚來源的專案，以及相對於全域來源的元素。|
|[uninitialized_object 類別](uninitialized-object-class.md)|當使用未初始化的物件時，所擲回的例外狀況。|
|[unsupported_feature 類別](unsupported-feature-class.md)|使用不支援的功能時，所擲回的例外狀況。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[access_type 列舉](concurrency-namespace-enums-amp.md#access_type)|指定資料存取類型。|
|[queuing_mode 列舉](concurrency-namespace-enums-amp.md#queuing_mode)|指定加速器支援的佇列模式。|

### <a name="operators"></a>運算子

|運算子|描述|
|--------------|-----------------|
|[operator = = 運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_eq_eq)|判斷指定的資料結構是否相等。|
|[operator！ = 運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_neq)|判斷指定的資料結構是否不相等。|
|[operator + 運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_add)|計算指定引數的元件成對總和。|
|[operator-運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator-)|計算指定引數之間的元件取向差異。|
|[operator * 運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_star)|計算指定引數的元件產品。|
|[operator/運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_div)|計算指定引數的元件的商。|
|[operator% 運算子（C++ AMP）](concurrency-namespace-operators-amp.md#operator_mod)|以第二個指定的引數來計算第一個指定引數的模數。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|封鎖磚中所有線程的執行，直到所有記憶體存取都完成為止。|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消初始化C++ AMP 執行時間。|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|已多載。 如果儲存在指定位置的值比較等於第一個指定的值，則第二個指定的值會儲存在與不可部分完成作業相同的位置。|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|已多載。 將儲存在指定位置的值設定為指定的值，做為不可部分完成的作業。|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|已多載。 將儲存在指定位置的值，設定為該值與指定值的總和，做為不可部分完成的作業。|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|已多載。 將儲存在指定位置的值，設定為該值的位 `and`，並將指定的值設為不可部分完成的運算。|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|已多載。 遞減儲存在指定位置的值，並將結果儲存在與不可部分完成作業相同的位置。|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|已多載。 遞增儲存在指定位置的值，並將結果儲存在與不可部分完成作業相同的位置。|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|已多載。 將儲存在指定位置的值設定為該值的較大值，並將指定的值設為不可部分完成的運算。|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|已多載。 將儲存在指定位置的值設定為該值的較小值，並將指定的值設為不可部分完成的運算。|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|已多載。 將儲存在指定位置的值，設定為該值的位 `or`，並將指定的值設為不可部分完成的運算。|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|已多載。 將儲存在指定位置的值，設定為該值與指定值的差異，做為不可部分完成的作業。|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|已多載。 將儲存在指定位置的值，設定為該值的位 `xor`，並將指定的值設為不可部分完成的運算。|
|[copy](concurrency-namespace-functions-amp.md#copy)|複製C++ AMP 物件。 符合所有同步資料傳輸需求。 當程式碼執行快速鍵上的程式碼時，無法複製資料。 此函式的一般形式為 `copy(src, dest)`。|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|複製C++ AMP 物件，並傳回可在上等候的[completion_future](completion-future-class.md) 。 當程式碼正在加速器上執行時，無法複製資料。 此函式的一般形式為 `copy(src, dest)`。|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止具有 `restrict(amp)` 限制子句的函數執行。|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|將格式化的字串列印到 Visual Studio 的**輸出**視窗，並引發具有相同格式字串的[runtime_exception](runtime-exception-class.md)例外狀況。|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|將格式化的字串列印到 Visual Studio 的 [**輸出**] 視窗。 它是從具有 `restrict(amp)` 限制子句的函式呼叫。|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|封鎖磚中所有線程的執行，直到所有全域記憶體存取都完成為止。|
|[parallel_for_each 函式C++ （AMP）](concurrency-namespace-functions-amp.md#parallel_for_each)|跨計算網域執行函數。|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|封鎖磚中所有線程的執行，直到完成 `tile_static` 記憶體存取為止。|

## <a name="constants"></a>常數

|名稱|描述|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 常數](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX 允許的緩衝區數目上限。|
|[MODULENAME_MAX_LENGTH 常數](concurrency-namespace-constants-amp.md#modulename_max_length)|儲存模組名稱的最大長度。 這個值在編譯器和執行時間上必須相同。|

## <a name="requirements"></a>需求

**標頭︰** amp.h

## <a name="see-also"></a>另請參閱

[參考 (C++ AMP)](reference-cpp-amp.md)

---
title: "Concurrency 命名空間函式 (AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
dev_langs:
- C++
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: a976cc06b49b10d5bb8dcecb10e114efdd89faa8
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency 命名空間函式 (AMP)
||||  
|-|-|-|  
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|  
|[atomic_exchange 函式 (c + + AMP)](#atomic_exchange)|[atomic_fetch_add 函式 (c + + AMP)](#atomic_fetch_add)|[atomic_fetch_and 函式 (c + + AMP)](#atomic_fetch_and)|  
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|  
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函式 (c + + AMP)](#atomic_fetch_or)|[atomic_fetch_sub 函式 (c + + AMP)](#atomic_fetch_sub)|  
|[atomic_fetch_xor 函式 (c + + AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|  
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|  
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函式 (c + + AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|  
  
##  <a name="all_memory_fence"></a>all_memory_fence  
 區塊執行的所有執行緒，直到完成為止的所有記憶體存取在磚中。 這可確保所有的記憶體存取會顯示 [執行緒] 磚中，在其他執行緒，而且程式的順序執行。  
  
```  
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Barrier`  
 `tile_barrier` 物件。  
  
##  <a name="amp_uninitialize"></a>amp_uninitialize  
 未初始化 c + + AMP 執行階段。 它是合法的應用程式存留期期間多次呼叫此函式。 呼叫任何呼叫此函式的 c + + AMP API afer 會重新初始化 c + + AMP 執行階段。 請注意，您不能使用 c + + AMP 物件上呼叫此函式，這樣做會導致未定義的行為。 此外，同時呼叫此函式和任何其他 AMP Api 就是不合法的而且會導致未定義的行為。  
  
```  
void __cdecl amp_uninitialize();
```  
  
##  <a name="atomic_compare_exchange"></a>atomic_compare_exchange  
 以不可分割方式比較儲存在記憶體位置中指定的值相等，其值為第二個指定的引數，第一個引數和值都是一樣，如果記憶體位置的值變更為第三個指定的引數。  
  
```  
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,  
    _Inout_ int* _Expected_value,  
    int value  
    ) restrict(amp)

 
inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,  
    _Inout_ unsigned int* _Expected_value,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 其中一個要比較的值的位置讀取，以及要新的值，如果有的話，會儲存。  
  
 `_Expected_value`  
 要比較的第二個值讀取位置。  
  
 `value`  
 要儲存至記憶體位置中所指定的值`_Dest`如果`_Dest`等於`_Expected_value`。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，則為 `true`，否則為 `false`。  
  

##  <a name="atomic_exchange"></a>atomic_exchange 函式 (c + + AMP)  
 設定目的地位置的值，成為不可部分完成的作業。  
  
```  
inline int atomic_exchange(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)

 
inline float atomic_exchange(
    _Inout_ float* _Dest,  
    float value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 之目的地位置指標。  
  
 `value`  
 新值。  
  
### <a name="return-value"></a>傳回值  
 目的地位置的原始值。  
  

##  <a name="atomic_fetch_add"></a>atomic_fetch_add 函式 (c + + AMP)  
 自動將值加入至記憶體位置的值。  
  
```  
inline int atomic_fetch_add(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 指標的記憶體位置。  
  
 `value`  
 要加入的值。  
  
### <a name="return-value"></a>傳回值  
 記憶體位置的原始值。  
  
##  <a name="atomic_fetch_and"></a>atomic_fetch_and 函式 (c + + AMP)  
 以原子方式執行值與的記憶體位置的值的位元 AND 運算。  
  
```  
inline int atomic_fetch_and(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 指標的記憶體位置。  
  
 `value`  
 要在位元 AND 計算中使用的值。  
  
### <a name="return-value"></a>傳回值  
 記憶體位置的原始值。  
  
##  <a name="atomic_fetch_dec"></a>atomic_fetch_dec  
 以不可分割方式遞減值儲存在指定的記憶體位置。  
  
```  
inline int atomic_fetch_dec(_Inout_ int* _Dest  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要遞減值的記憶體中的位置。  
  
### <a name="return-value"></a>傳回值  
 儲存在記憶體位置的原始值。  
  
##  <a name="atomic_fetch_inc"></a>atomic_fetch_inc  
 自動遞增的值儲存在指定的記憶體位置。  
  
```  
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

 
inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要遞增之值的記憶體中的位置。  
  
### <a name="return-value"></a>傳回值  
 儲存在記憶體位置的原始值。  
  
##  <a name="atomic_fetch_max"></a>atomic_fetch_max  
 自動計算值儲存在第一個引數和第二個引數中指定的值中指定的記憶體位置之間的最大值，並將它儲存在相同的記憶體位置。  
  
```  
inline int atomic_fetch_max(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 在讀取其中一個要比較的值的位置，以及這兩個值的最大值是儲存。  
  
 `value`  
 要比較的值，指定位置的值。  
  
### <a name="return-value"></a>傳回值  
 原始的值儲存在指定的位置。  
  
##  <a name="atomic_fetch_min"></a>atomic_fetch_min  
 自動計算值儲存在第一個引數和第二個引數中指定的值中指定的記憶體位置之間的最小值，並將它儲存在相同的記憶體位置。  
  
```  
inline int atomic_fetch_min(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 在讀取其中一個要比較的值的位置，以及這兩個值的最小值是儲存。  
  
 `value`  
 要比較的值，指定位置的值。  
  
### <a name="return-value"></a>傳回值  
 原始的值儲存在指定的位置。  
  
##  <a name="atomic_fetch_or"></a>atomic_fetch_or 函式 (c + + AMP)  
 以原子方式執行值，記憶體位置的值的位元 OR 運算。  
  
```  
inline int atomic_fetch_or(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 指標的記憶體位置。  
  
 `value`  
 要在位元的 OR 計算中使用的值。  
  
### <a name="return-value"></a>傳回值  
 記憶體位置的原始值。  
  
##  <a name="atomic_fetch_sub"></a>atomic_fetch_sub 函式 (c + + AMP)  
 以不可分割方式相減的記憶體位置的值。  
  
```  
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 之目的地位置指標。  
  
 `value`  
 要減去的值。  
  
### <a name="return-value"></a>傳回值  
 記憶體位置的原始值。  
  
##  <a name="atomic_fetch_xor"></a>atomic_fetch_xor 函式 (c + + AMP)  
 以不可分割方式 peforms 值和記憶體位置的位元 XOR 運算。  
  
```  
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 指標的記憶體位置。  
  
 `value`  
 要在 XOR 計算中使用的值。  
  
### <a name="return-value"></a>傳回值  
 記憶體位置的原始值。  
  
##  <a name="copy"></a> copy  
 將 c + + AMP 物件複製。 符合所有同步的資料傳輸需求。 加速器上執行的程式碼時，您無法複製資料。 此函式的一般形式是`copy(src, dest)`。  
  
```  
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,
     OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst, 
    InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要複製到的物件。  
  
 `_DestIter`  
 目的地端的開頭位置輸出迭代器。  
  
 `InputIterator`  
 輸入 interator 型別。  
  
 `OutputIterator`  
 輸出迭代器類型。  
  
 `_Rank`  
 要複製的物件或物件複製到陣序規範。  
  
 `_Src`  
 若要複製的物件。  
  
 `_SrcFirst`  
 在來源容器的開頭迭代器。  
  
 `_SrcLast`  
 結束迭代器，為來源容器。  
  
 `value_type`  
 複製的項目資料型別。  
  
##  <a name="copy_async"></a>copy_async  
 複製 c + + AMP 物件並傳回[completion_future](completion-future-class.md)可以等候的物件。 加速器上執行的程式碼時，您無法複製資料。  此函式的一般形式是`copy(src, dest)`。  
  
```  
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要複製到的物件。  
  
 `_DestIter`  
 目的地端的開頭位置輸出迭代器。  
  
 `InputIterator`  
 輸入 interator 型別。  
  
 `OutputIterator`  
 輸出迭代器類型。  
  
 `_Rank`  
 要複製的物件或物件複製到陣序規範。  
  
 `_Src`  
 若要複製的物件。  
  
 `_SrcFirst`  
 在來源容器的開頭迭代器。  
  
 `_SrcLast`  
 結束迭代器，為來源容器。  
  
 `value_type`  
 複製的項目資料型別。  
  
### <a name="return-value"></a>傳回值  
 A`future<void>`可以等候的。  
  
##  <a name="direct3d_abort"></a>direct3d_abort  
 使用 `restrict(amp)` 限制子句中止函式執行。 AMP 執行階段偵測到在呼叫時，它會引發[runtime_exception](runtime-exception-class.md)例外狀況，並出現錯誤訊息 「 參考光柵處理器︰ 著色器中止指令叫用 」。  
  
```  
void direct3d_abort() restrict(amp);
```  
  
##  <a name="direct3d_errorf"></a>direct3d_errorf  
 列印 Visual Studio 的 輸出 視窗的格式化的字串。 呼叫的函式從`restrict(amp)`限制子句。 AMP 執行階段偵測到在呼叫時，它會引發[runtime_exception](runtime-exception-class.md)使用相同的格式字串的例外狀況。  
  
```  
void direct3d_errorf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="direct3d_printf"></a>direct3d_printf  
 列印 Visual Studio 的 輸出 視窗的格式化的字串。 呼叫的函式從`restrict(amp)`限制子句。  
  
```  
void direct3d_printf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="global_memory_fence"></a>global_memory_fence  
 已完成的所有執行緒，直到所有的全域記憶體存取在磚中的區塊執行。 這可確保全域記憶體存取會顯示 [執行緒] 磚中，在其他執行緒，而且程式的順序執行。  
  
```  
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Barrier`  
 Tile_barrier 物件  
  
##  <a name="parallel_for_each"></a>parallel_for_each 函式 (c + + AMP)  
 在計算網域中執行的函式。 如需詳細資訊，請參閱[c + + AMP 概觀](../../../parallel/amp/cpp-amp-overview.md)。  
  
```  
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
     const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);
```  
  
### <a name="parameters"></a>參數  
 `_Accl_view`  
 `accelerator_view`物件上執行平行計算。  
  
 `_Compute_domain`  
 `extent`包含計算資料的物件。  
  
 `_Dim0`  
 維度的`tiled_extent`物件。  
  
 `_Dim1`  
 維度的`tiled_extent`物件。  
  
 `_Dim2`  
 維度的`tiled_extent`物件。  
  
 `_Kernel`  
 使用型別的引數的 lambda 或函式物件 」 索引\<_Rank > 」 並執行平行計算。  
  
 `_Kernel_type`  
 Lambda 或仿函式中。  
  
 `_Rank`  
 範圍的陣序規範。  
  
##  <a name="tile_static_memory_fence"></a>tile_static_memory_fence  
 阻礙磚中的所有執行緒的執行，直到所有未完成`tile_static`已完成的記憶體存取。 這可確保`tile_static`記憶體存取會顯示在 [執行緒] 磚，其他執行緒，而且存取執行中程式的順序。  
  
```  
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Barrier`  
 Tile_barrier 物件。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)


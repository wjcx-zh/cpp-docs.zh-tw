---
title: Concurrency 命名空間函式 (AMP)
ms.date: 11/04/2016
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
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 43be1fc3a5df52f6edcc05b501b1463bd5da7e6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481792"
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

##  <a name="all_memory_fence"></a>  all_memory_fence

所有的執行緒，直到所有記憶體存取都已經都完成的區塊執行。 這可確保所有記憶體存取對執行緒 tile 中，在其他執行緒可見，而且依照程式順序執行。

```
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
`tile_barrier` 物件。

##  <a name="amp_uninitialize"></a>  amp_uninitialize

取消初始化 c + + AMP 執行階段。 它是合法的應用程式存留期間多次呼叫此函式。 呼叫任何呼叫此函式的 c + + AMP API 之後，將會重新初始化 c + + AMP 執行階段。 請注意，是在呼叫此函式中使用 c + + AMP 物件不合法的這樣做會導致未定義的行為。 此外，同時呼叫此函式和任何其他 AMP Api 就是不合法的而且會導致未定義的行為。

```
void __cdecl amp_uninitialize();
```

##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange

以不可分割方式比較儲存在記憶體位置中指定的值相等的值為第二個指定的引數，第一個引數，如果值相同，記憶體位置的值變更為第三個指定引數。

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

*_Dest*<br/>
其中一個要比較的值的位置所讀取，以及要新增的值，如果有的話，是儲存。

*_Expected_value*<br/>
要從中讀取要比較的第二個值的位置。

*值*<br/>
要儲存至指定的記憶體位置的值`_Dest`如果`_Dest`等於`_Expected_value`。

### <a name="return-value"></a>傳回值

**真**如果作業成功，否則**false**。

##  <a name="atomic_exchange"></a>  atomic_exchange 函式 (c + + AMP)

設定目的地位置的值做為不可部分完成的作業。

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

*_Dest*<br/>
目的地位置的指標。

*值*<br/>
新值。

### <a name="return-value"></a>傳回值

目的地位置的原始值。

##  <a name="atomic_fetch_add"></a>  atomic_fetch_add 函式 (c + + AMP)

以不可分割方式加入值的記憶體位置的值。

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

*_Dest*<br/>
記憶體位置指標。

*值*<br/>
要加入的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

##  <a name="atomic_fetch_and"></a>  atomic_fetch_and 函式 (c + + AMP)

以不可分割方式執行位元 AND 運算的值以及記憶體位置的值。

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

*_Dest*<br/>
記憶體位置指標。

*值*<br/>
要使用位元的 AND 計算中的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec

以不可分割方式遞減值儲存在指定的記憶體位置。

```
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞減之值的記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc

以不可分割方式遞增儲存於指定的記憶體位置的值。

```
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞增之值的記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

##  <a name="atomic_fetch_max"></a>  atomic_fetch_max

以不可分割方式計算儲存在第一個引數和第二個引數中指定的值中指定的記憶體位置的值之間的最大值，並將其儲存在相同的記憶體位置。

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

*_Dest*<br/>
其中一個要比較的值讀取自，以及位置這兩個值的最大值是儲存。

*值*<br/>
要在指定位置的值相比較的值。

### <a name="return-value"></a>傳回值

儲存在指定之的位置的原始值。

##  <a name="atomic_fetch_min"></a>  atomic_fetch_min

以不可分割方式計算儲存在第一個引數和第二個引數中指定的值中指定的記憶體位置的值之間的最小值，並將其儲存在相同的記憶體位置。

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

*_Dest*<br/>
其中一個要比較的值讀取自，以及位置這兩個值的最小值是儲存。

*值*<br/>
要在指定位置的值相比較的值。

### <a name="return-value"></a>傳回值

儲存在指定之的位置的原始值。

##  <a name="atomic_fetch_or"></a>  atomic_fetch_or 函式 (c + + AMP)

以不可分割方式執行位元的 OR 運算的值以及記憶體位置的值。

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

*_Dest*<br/>
記憶體位置指標。

*值*<br/>
要使用位元的 OR 計算中的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

##  <a name="atomic_fetch_sub"></a>  atomic_fetch_sub 函式 (c + + AMP)

以不可分割方式減去的記憶體位置的值。

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

*_Dest*<br/>
目的地位置的指標。

*值*<br/>
要減去的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

##  <a name="atomic_fetch_xor"></a>  atomic_fetch_xor 函式 (c + + AMP)

以不可分割方式 peforms 值與的記憶體位置的位元 XOR 運算。

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

*_Dest*<br/>
記憶體位置指標。

*值*<br/>
要在 XOR 計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

##  <a name="copy"></a>  copy

複製 c + + AMP 物件。 已符合所有的同步資料傳輸需求。 在加速器上執行的程式碼時，您無法複製資料。 此函式的一般形式是`copy(src, dest)`。

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

*_Dest*<br/>
要複製到的物件。

*_DestIter*<br/>
目的地端的起始位置的輸出迭代器。

*InputIterator*<br/>
輸入迭代器類型。

*OutputIterator*<br/>
輸出迭代器類型。

*_Rank*<br/>
要複製的物件或複製到物件的順位。

*_Src*<br/>
若要複製的物件。

*_SrcFirst*<br/>
來源容器中的開頭迭代器。

*_SrcLast*<br/>
來源容器中結束迭代器。

*value_type*<br/>
複製的項目資料型別。

##  <a name="copy_async"></a>  copy_async

複製 c + + AMP 物件並傳回[completion_future](completion-future-class.md)可以等候的物件。 在加速器上執行的程式碼時，您無法複製資料。  此函式的一般形式是`copy(src, dest)`。

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

*_Dest*<br/>
要複製到的物件。

*_DestIter*<br/>
目的地端的起始位置的輸出迭代器。

*InputIterator*<br/>
輸入迭代器類型。

*OutputIterator*<br/>
輸出迭代器類型。

*_Rank*<br/>
要複製的物件或複製到物件的順位。

*_Src*<br/>
若要複製的物件。

*_SrcFirst*<br/>
來源容器中的開頭迭代器。

*_SrcLast*<br/>
來源容器中結束迭代器。

*value_type*<br/>
複製的項目資料型別。

### <a name="return-value"></a>傳回值

A`future<void>`可以等候。

##  <a name="direct3d_abort"></a>  direct3d_abort

使用 `restrict(amp)` 限制子句中止函式執行。 當 AMP 執行階段偵測到呼叫時，會引發 [runtime_exception](runtime-exception-class.md) 例外狀況，並顯示錯誤訊息 "Reference Rasterizer: Shader abort instruction hit"。

```
void direct3d_abort() restrict(amp);
```

##  <a name="direct3d_errorf"></a>  direct3d_errorf

列印格式化的字串，Visual Studio 的 [輸出] 視窗。 呼叫的函式從`restrict(amp)`限制子句。 當 AMP 執行階段偵測到呼叫時，會引發[runtime_exception](runtime-exception-class.md)例外狀況，相同的格式字串。

```
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

##  <a name="direct3d_printf"></a>  direct3d_printf

列印格式化的字串，Visual Studio 的 [輸出] 視窗。 呼叫的函式從`restrict(amp)`限制子句。

```
void direct3d_printf(
    const char *,
...) restrict(amp);
```

##  <a name="global_memory_fence"></a>  global_memory_fence

封鎖直到所有全域記憶體存取的所有執行緒的執行已完成。 這可確保全域記憶體存取對執行緒 tile 中，在其他執行緒可見，而且依照程式順序執行。

```
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件

##  <a name="parallel_for_each"></a>  parallel_for_each 函式 (c + + AMP)

整個計算網域中執行的函式。 如需詳細資訊，請參閱 < [c + + AMP 概觀](../../../parallel/amp/cpp-amp-overview.md)。

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

*_Accl_view*<br/>
`accelerator_view`物件執行平行計算。

*_Compute_domain*<br/>
`extent`物件，其中包含計算的資料。

*_Dim0*<br/>
維度的`tiled_extent`物件。

*_Dim1*<br/>
維度的`tiled_extent`物件。

*_Dim2*<br/>
維度的`tiled_extent`物件。

*_Kernel*<br/>
接受類型引數的 lambda 或函式物件 」 索引\<_Rank >"，並執行平行計算。

*_Kernel_type*<br/>
Lambda 或仿函式中。

*_Rank*<br/>
範圍的順位。

##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence

封鎖 tile 中的所有執行緒的執行，直到所有未完成`tile_static`記憶體存取都已經完成。 這可確保`tile_static`記憶體存取對執行緒 tile 中，在其他執行緒可見，而且存取依照程式順序執行。

```
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

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
ms.openlocfilehash: b03a6189d2205dff62d94f07bc597ca2e1013a28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840202"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency 命名空間函式 (AMP)

:::row:::
   :::column span="":::
      [`all_memory_fence`](#all_memory_fence)\
      [`amp_uninitialize`](#amp_uninitialize)\
      [`atomic_compare_exchange`](#atomic_compare_exchange)\
      [`atomic_exchange`](#atomic_exchange)\
      [`atomic_fetch_add`](#atomic_fetch_add)\
      [`atomic_fetch_and`](#atomic_fetch_and)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_dec`](#atomic_fetch_dec)\
      [`atomic_fetch_inc`](#atomic_fetch_inc)\
      [`atomic_fetch_max`](#atomic_fetch_max)\
      [`atomic_fetch_min`](#atomic_fetch_min)\
      [`atomic_fetch_or`](#atomic_fetch_or)
   :::column-end:::
   :::column span="":::
      [`atomic_fetch_sub`](#atomic_fetch_sub)\
      [`atomic_fetch_xor`](#atomic_fetch_xor)\
      [`copy`](#copy)\
      [`copy_async`](#copy_async)\
      [`direct3d_abort`](#direct3d_abort)
   :::column-end:::
   :::column span="":::
      [`direct3d_errorf`](#direct3d_errorf)\
      [`direct3d_printf`](#direct3d_printf)\
      [`global_memory_fence`](#global_memory_fence)\
      [`parallel_for_each`](#parallel_for_each)\
      [`tile_static_memory_fence`](#tile_static_memory_fence)
   :::column-end:::
:::row-end:::

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a> all_memory_fence

封鎖磚中所有線程的執行，直到所有記憶體存取都完成為止。 這可確保執行緒磚中的其他執行緒可以看到所有記憶體存取，並依程式循序執行。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
`tile_barrier` 物件。

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a> amp_uninitialize

取消初始化 C++ AMP 執行時間。 在應用程式存留期間多次呼叫此函式是合法的。 呼叫此函式之後，呼叫任何 C++ AMP API 將會重新初始化 C++ AMP 執行時間。 請注意，在呼叫此函式時使用 C++ AMP 物件是不合法的，而且這麼做會導致未定義的行為。 此外，同時呼叫這個函式和任何其他 AMP Api 都是不合法的，而且會導致未定義的行為。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a> atomic_compare_exchange

以不可部分完成的方式，將第一個引數所指定的記憶體位置所儲存的值與第二個指定引數的值進行比較，如果值相同，則記憶體位置的值會變更為第三個指定引數的值。

```cpp
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
要從中比較其中一個值的位置，以及要儲存新值的位置（如果有的話）。

*_Expected_value*<br/>
要進行比較的第二個值的來源位置。

*value*<br/>
如果等於，則為要儲存至中指定之記憶體位置的值 `_Dest` `_Dest` `_Expected_value` 。

### <a name="return-value"></a>傳回值

**`true`** 如果作業成功，則為，否則為 **`false`** 。

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a> atomic_exchange 函式 (C++ AMP) 

將目的地位置的值設定為不可部分完成的作業。

```cpp
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

*value*<br/>
新值。

### <a name="return-value"></a>傳回值

目的地位置的原始值。

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a> atomic_fetch_add 函式 (C++ AMP) 

以不可部分完成的方式將值加入至記憶體位置的值。

```cpp
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
記憶體位置的指標。

*value*<br/>
要加入的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a> atomic_fetch_and 函式 (C++ AMP) 

以不可部分完成的方式執行值的位 AND 運算，以及記憶體位置的值。

```cpp
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
記憶體位置的指標。

*value*<br/>
要在位 AND 運算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a> atomic_fetch_dec

以不可部分完成的方式遞減儲存在指定之記憶體位置的值。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞減之值在記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a> atomic_fetch_inc

以不可部分完成的方式遞增儲存在指定之記憶體位置的值。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞增的值在記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a> atomic_fetch_max

以不可部分完成的方式，在第一個引數所指定之記憶體位置的值和第二個引數中指定的值之間，計算值之間的最大值，並將它儲存在相同的記憶體位置。

```cpp
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
要從中比較其中一個值的位置，以及要儲存這兩個值最大值的位置。

*value*<br/>
要與指定位置上的值比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置位置的原始值。

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a> atomic_fetch_min

以不可部分完成的方式，計算儲存在第一個引數指定的記憶體位置值與第二個引數中指定的值之間的最小值，並將它儲存在相同的記憶體位置。

```cpp
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
要從中比較其中一個值的位置，以及要儲存這兩個值最小值的位置。

*value*<br/>
要與指定位置上的值比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置位置的原始值。

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a> atomic_fetch_or 函式 (C++ AMP) 

使用值和記憶體位置的值，以自動方式執行位 OR 運算。

```cpp
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
記憶體位置的指標。

*value*<br/>
要在位 OR 運算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a> atomic_fetch_sub 函式 (C++ AMP) 

以不可部分完成的方式減去記憶體位置的值。

```cpp
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

*value*<br/>
要減去的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a> atomic_fetch_xor 函式 (C++ AMP) 

以不可部分完成的方式執行值和記憶體位置的位 XOR 運算。

```cpp
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
記憶體位置的指標。

*value*<br/>
XOR 計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="copy"></a><a name="copy"></a> 複製

複製 C++ AMP 物件。 符合所有的同步資料傳輸需求。 您無法在加速器上執行程式碼時複製資料。 此函數的一般形式為 `copy(src, dest)` 。

```cpp
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
要複製的物件。

*_DestIter*<br/>
目的地端開始位置的輸出反覆運算器。

*InputIterator*<br/>
輸入迭代器的類型。

*Outputiterator>*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製之物件的順位或要複製到其中的物件。

*_Src*<br/>
要複製的物件。

*_SrcFirst*<br/>
來源容器中的開始反覆運算器。

*_SrcLast*<br/>
來源容器中的結束反覆運算器。

*value_type*<br/>
複製之元素的資料類型。

## <a name="copy_async"></a><a name="copy_async"></a> copy_async

複製 C++ AMP 物件，並傳回可等候的 [completion_future](completion-future-class.md) 物件。 您無法在加速器上執行程式碼時複製資料。  此函數的一般形式為 `copy(src, dest)` 。

```cpp
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
要複製的物件。

*_DestIter*<br/>
目的地端開始位置的輸出反覆運算器。

*InputIterator*<br/>
輸入迭代器的類型。

*Outputiterator>*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製之物件的順位或要複製到其中的物件。

*_Src*<br/>
要複製的物件。

*_SrcFirst*<br/>
來源容器中的開始反覆運算器。

*_SrcLast*<br/>
來源容器中的結束反覆運算器。

*value_type*<br/>
複製之元素的資料類型。

### <a name="return-value"></a>傳回值

`future<void>`可以等候的。

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a> direct3d_abort

使用 `restrict(amp)` 限制子句中止函式執行。 當 AMP 執行階段偵測到呼叫時，會引發 [runtime_exception](runtime-exception-class.md) 例外狀況，並顯示錯誤訊息 "Reference Rasterizer: Shader abort instruction hit"。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a> direct3d_errorf

將格式化的字串列印到 Visual Studio 的輸出視窗。 它會從具有限制子句的函式中呼叫 `restrict(amp)` 。 當 AMP 執行時間偵測到呼叫時，會引發具有相同格式字串的 [runtime_exception](runtime-exception-class.md) 例外狀況。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a> direct3d_printf

將格式化的字串列印到 Visual Studio 的輸出視窗。 它會從具有限制子句的函式中呼叫 `restrict(amp)` 。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a> global_memory_fence

封鎖磚中所有線程的執行，直到所有的全域記憶體存取都完成為止。 這可確保執行緒磚中的其他執行緒可以看到全域記憶體存取，並以程式循序執行。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a> parallel_for_each 函式 (C++ AMP) 

跨計算網域執行函數。 如需詳細資訊，請參閱 [C++ AMP 總覽](../../../parallel/amp/cpp-amp-overview.md)。

```cpp
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
`accelerator_view`要在其上執行平行計算的物件。

*_Compute_domain*<br/>
`extent`包含計算資料的物件。

*_Dim0*<br/>
物件的維度 `tiled_extent` 。

*_Dim1*<br/>
物件的維度 `tiled_extent` 。

*_Dim2*<br/>
物件的維度 `tiled_extent` 。

*_Kernel*<br/>
Lambda 或函式物件，該物件會接受 "index" 類型的引數 \<_Rank> ，並執行平行計算。

*_Kernel_type*<br/>
Lambda 或仿函數。

*_Rank*<br/>
範圍的等級。

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a> tile_static_memory_fence

封鎖磚中所有線程的執行，直到所有未完成的 `tile_static` 記憶體存取都完成為止。 這可確保 `tile_static` 執行緒磚中的其他執行緒可以看到記憶體存取，而且會以程式循序執行存取。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件。

## <a name="see-also"></a>另請參閱

[並行命名空間 (C++ AMP) ](concurrency-namespace-cpp-amp.md)

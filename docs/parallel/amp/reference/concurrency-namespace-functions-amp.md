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
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376343"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency 命名空間函式 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 函式 (C++ AMP)](#atomic_exchange)|[atomic_fetch_add 函式 (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and 函式 (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函式 (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub功能(C++安培)](#atomic_fetch_sub)|
|[atomic_fetch_xor 函式 (C++ AMP)](#atomic_fetch_xor)|[複製](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函式 (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

阻止執行磁貼中的所有線程,直到完成所有記憶體訪問。 這可確保線程磁貼中的其他線程對所有記憶體訪問都可見,並且按程式順序執行。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
`tile_barrier` 物件。

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

取消初始化C++ AMP運行時。 在應用程式生存期內多次調用此函數是合法的。 調用此函數後調用任何C++ AMP API 將重新初始化 C++ AMP 運行時。 請注意,跨調用此函數C++ AMP 對像是非法的,這樣做將導致未定義的行為。 此外,同時調用此函數和任何其他 AMP API 是非法的,將導致未定義的行為。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

原子方式將存儲在第一個參數中指定的記憶體位置的值與第二個指定參數的值進行比較,如果值相同,則記憶體位置的值將更改為第三個指定參數的值。

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
讀取要比較的一個值的位置,以及要存儲新值(如果有)的位置。

*_Expected_value*<br/>
讀取要比較的第二個值的位置。

*值*<br/>
要儲存到的記憶體位置的值,`_Dest`如果`_Dest`等於`_Expected_value`。

### <a name="return-value"></a>傳回值

如果操作成功,**為 true;** 否則,**假**。

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>atomic_exchange功能(C++安培)

將目標位置的值作為原子操作設置。

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
指向目標位置的指標。

*值*<br/>
新的值。

### <a name="return-value"></a>傳回值

目標位置的原始值。

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>atomic_fetch_add功能(C++安培)

以原子方式向記憶體位置的值添加值。

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
指向記憶體位置的指標。

*值*<br/>
要加入的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>atomic_fetch_and功能(C++安培)

原子上執行值和記憶體位置的值的位和操作。

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
指向記憶體位置的指標。

*值*<br/>
要在位元和計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

從原子上遞減存儲在指定記憶體位置的值。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞減的值的記憶體中的位置。

### <a name="return-value"></a>傳回值

存儲在記憶體位置的原始值。

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

以原子方式增加存儲在指定記憶體位置的值。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞增的值的記憶體中的位置。

### <a name="return-value"></a>傳回值

存儲在記憶體位置的原始值。

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

原子計算存儲在第一個參數中指定的記憶體位置的值和第二個參數中指定的值之間的最大值,並將其存儲在相同的記憶體位置。

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
讀取要比較的一個值的位置,以及將兩個值的最大值存儲到的位置。

*值*<br/>
要與指定位置的值進行比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置的原始值。

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

以原子方式計算存儲在第一個參數中指定的記憶體位置的值和第二個參數中指定的值之間的最小值,並將其存儲在相同的記憶體位置。

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
讀取要比較的一個值的位置,以及要存儲兩個值的最小值的位置。

*值*<br/>
要與指定位置的值進行比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置的原始值。

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>atomic_fetch_or功能(C++安培)

原子上執行具有值和記憶體位置值的位或操作。

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
指向記憶體位置的指標。

*值*<br/>
要在位元或計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub功能(C++安培)

從記憶體位置以原子方式減去值。

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
指向目標位置的指標。

*值*<br/>
要減去的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor功能(C++安培)

原子上執行值和記憶體位置的位 XOR 操作。

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
指向記憶體位置的指標。

*值*<br/>
要在 XOR 計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="copy"></a><a name="copy"></a>複製

複製C++ AMP 物件。 滿足所有同步數據傳輸要求。 在加速器上運行代碼時,無法複製數據。 此函數的一般形式是`copy(src, dest)`。

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
到目標處開始位置的輸出反覆運算器。

*輸入反覆運算器*<br/>
輸入迭代器的類型。

*輸出反覆運算器*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製的物件的排名或要複製到的物件。

*_Src*<br/>
以反對複製。

*_SrcFirst*<br/>
到源容器的開始反覆運算器。

*_SrcLast*<br/>
到源容器的結束反覆運算器。

*value_type*<br/>
複製的元素的數據類型。

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

複製C++ AMP 物件並返回可以等待[的物件completion_future。](completion-future-class.md) 在加速器上運行代碼時,無法複製數據。  此函數的一般形式是`copy(src, dest)`。

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
到目標處開始位置的輸出反覆運算器。

*輸入反覆運算器*<br/>
輸入迭代器的類型。

*輸出反覆運算器*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製的物件的排名或要複製到的物件。

*_Src*<br/>
以反對複製。

*_SrcFirst*<br/>
到源容器的開始反覆運算器。

*_SrcLast*<br/>
到源容器的結束反覆運算器。

*value_type*<br/>
複製的元素的數據類型。

### <a name="return-value"></a>傳回值

`future<void>`可以等待的。

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

使用 `restrict(amp)` 限制子句中止函式執行。 當 AMP 執行階段偵測到呼叫時，會引發 [runtime_exception](runtime-exception-class.md) 例外狀況，並顯示錯誤訊息 "Reference Rasterizer: Shader abort instruction hit"。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

將格式化的字串列印到視覺化工作室輸出視窗。 它從具有限制子句的`restrict(amp)`函數調用。 當 AMP 執行時檢測到調用時,它會引發具有相同格式字串[runtime_exception](runtime-exception-class.md)異常。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

將格式化的字串列印到視覺化工作室輸出視窗。 它從具有限制子句的`restrict(amp)`函數調用。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

阻止執行磁貼中的所有線程,直到完成所有全域記憶體訪問。 這可確保全域記憶體訪問對線程磁貼中的其他線程可見,並且按程式順序執行。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
tile_barrier物件

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>parallel_for_each功能(C++安培)

跨計算域運行函數。 有關詳細資訊,請參閱[C++ AMP 概述](../../../parallel/amp/cpp-amp-overview.md)。

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
要`accelerator_view`運行並行計算的物件。

*_Compute_domain*<br/>
包含`extent`計算數據的物件。

*_Dim0*<br/>
`tiled_extent`對象的維度。

*_Dim1*<br/>
`tiled_extent`對象的維度。

*_Dim2*<br/>
`tiled_extent`對象的維度。

*_Kernel*<br/>
採用類型為「索引\<_Rank>」並執行並行計算的參數的 lambda 或函數物件。

*_Kernel_type*<br/>
羊羔或娛樂。

*_Rank*<br/>
範圍的等級。

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

阻止執行磁貼中的所有線程,直到完成所有未完成的`tile_static`記憶體訪問。 這可確保`tile_static`記憶體訪問對線程磁貼中的其他線程可見,並且按程式順序執行訪問。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
tile_barrier物件。

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)

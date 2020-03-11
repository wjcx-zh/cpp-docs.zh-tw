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
ms.openlocfilehash: 90a23ce111f7307610de3f0ad4bcec05d8de27df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855721"
---
# <a name="concurrency-namespace-functions-amp"></a>Concurrency 命名空間函式 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 函式C++ （AMP）](#atomic_exchange)|[atomic_fetch_add 函式C++ （AMP）](#atomic_fetch_add)|[atomic_fetch_and 函式C++ （AMP）](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函式C++ （AMP）](#atomic_fetch_or)|[atomic_fetch_sub 函式C++ （AMP）](#atomic_fetch_sub)|
|[atomic_fetch_xor 函式C++ （AMP）](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函式C++ （AMP）](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a>all_memory_fence

封鎖磚中所有線程的執行，直到所有記憶體存取都完成為止。 這可確保 [執行緒] 磚中的其他執行緒可以看見所有的記憶體存取，並以程式循序執行。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
`tile_barrier` 物件。

## <a name="amp_uninitialize"></a>amp_uninitialize

取消初始化C++ AMP 執行時間。 在應用程式存留期間，多次呼叫此函式是合法的。 呼叫此C++函式後呼叫任何 AMP API 將會C++重新初始化 amp 執行時間。 請注意，在呼叫此函C++式時使用 AMP 物件是不合法的，這樣做會導致未定義的行為。 此外，同時呼叫此函式和任何其他 AMP Api 並不合法，而且會導致未定義的行為。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a>atomic_compare_exchange

會以自動方式比較第一個引數中指定的記憶體位置所儲存的值是否等於第二個指定引數的值; 如果值相同，則記憶體位置的值會變更為第三個指定引數的值。

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
要進行比較的其中一個值的位置，以及要儲存的新值（如果有的話）。

*_Expected_value*<br/>
要進行比較之第二個值的讀取位置。

*value*<br/>
如果 `_Dest` 等於 `_Expected_value`，要儲存在中指定之記憶體位置的值 `_Dest`。

### <a name="return-value"></a>傳回值

如果作業成功，則為**true** ;否則**為 false**。

## <a name="atomic_exchange"></a>atomic_exchange 函式C++ （AMP）

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
新的值。

### <a name="return-value"></a>傳回值

目的地位置的原始值。

## <a name="atomic_fetch_add"></a>atomic_fetch_add 函式C++ （AMP）

以原子方式將值新增至記憶體位置的值。

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
要新增的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_and"></a>atomic_fetch_and 函式C++ （AMP）

以原子方式執行值的位 AND 運算，以及記憶體位置的值。

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
要在位 AND 計算中使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="atomic_fetch_dec"></a>atomic_fetch_dec

以原子方式遞減儲存在指定記憶體位置的值。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞減的值在記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

## <a name="atomic_fetch_inc"></a>atomic_fetch_inc

以原子方式遞增儲存在指定記憶體位置的值。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要遞增的值在記憶體中的位置。

### <a name="return-value"></a>傳回值

儲存在記憶體位置的原始值。

## <a name="atomic_fetch_max"></a>atomic_fetch_max

以自動方式計算儲存在第一個引數中指定的記憶體位置和第二個引數中指定的值之間的最大值，並將它儲存在相同的記憶體位置。

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
要進行比較的其中一個值的位置，以及要儲存兩個值的最大值。

*value*<br/>
要與指定位置的值比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置位置的原始值。

## <a name="atomic_fetch_min"></a>atomic_fetch_min

以原子方式計算儲存在第一個引數中指定之記憶體位置的值和第二個引數中指定的值之間的最小值，並將它儲存在相同的記憶體位置。

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
要進行比較的其中一個值的位置，以及要儲存兩個值的最小值。

*value*<br/>
要與指定位置的值比較的值。

### <a name="return-value"></a>傳回值

儲存在指定位置位置的原始值。

## <a name="atomic_fetch_or"></a>atomic_fetch_or 函式C++ （AMP）

使用值和記憶體位置的值，以原子方式執行位 OR 運算。

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

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub 函式C++ （AMP）

以不可部分完成的方式，從記憶體位置減去值。

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

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor 函式C++ （AMP）

以原子方式執行值和記憶體位置的位 XOR 運算。

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
XOR 計算中要使用的值。

### <a name="return-value"></a>傳回值

記憶體位置的原始值。

## <a name="copy"></a> copy

複製C++ AMP 物件。 符合所有同步資料傳輸需求。 在加速器上執行程式碼時，您無法複製資料。 此函式的一般形式為 `copy(src, dest)`。

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
目的地上開始位置的輸出反覆運算器。

*InputIterator*<br/>
輸入迭代器的類型。

*OutputIterator*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製之物件的次序或要複製的物件。

*_Src*<br/>
To 要複製的物件。

*_SrcFirst*<br/>
來源容器中的開始反覆運算器。

*_SrcLast*<br/>
來源容器中的結束反覆運算器。

*value_type*<br/>
複製之元素的資料類型。

## <a name="copy_async"></a>copy_async

複製C++ AMP 物件，並傳回可在其上等候的[completion_future](completion-future-class.md)物件。 在加速器上執行程式碼時，您無法複製資料。  此函式的一般形式為 `copy(src, dest)`。

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
目的地上開始位置的輸出反覆運算器。

*InputIterator*<br/>
輸入迭代器的類型。

*OutputIterator*<br/>
輸出反覆運算器的類型。

*_Rank*<br/>
要複製之物件的次序或要複製的物件。

*_Src*<br/>
To 要複製的物件。

*_SrcFirst*<br/>
來源容器中的開始反覆運算器。

*_SrcLast*<br/>
來源容器中的結束反覆運算器。

*value_type*<br/>
複製之元素的資料類型。

### <a name="return-value"></a>傳回值

可以等候的 `future<void>`。

## <a name="direct3d_abort"></a>direct3d_abort

使用 `restrict(amp)` 限制子句中止函式執行。 當 AMP 執行階段偵測到呼叫時，會引發 [runtime_exception](runtime-exception-class.md) 例外狀況，並顯示錯誤訊息 "Reference Rasterizer: Shader abort instruction hit"。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a>direct3d_errorf

將格式化的字串列印到 Visual Studio 的 [輸出] 視窗。 它是從具有 `restrict(amp)` 限制子句的函式中呼叫。 當 AMP 執行時間偵測到呼叫時，它會使用相同的格式字串來引發[runtime_exception](runtime-exception-class.md)例外狀況。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a>direct3d_printf

將格式化的字串列印到 Visual Studio 的 [輸出] 視窗。 它是從具有 `restrict(amp)` 限制子句的函式中呼叫。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a>global_memory_fence

封鎖磚中所有線程的執行，直到所有全域記憶體存取都完成為止。 這可確保 [執行緒] 磚中的其他執行緒可以看見全域記憶體存取，而且會依程式循序執行。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件

## <a name="parallel_for_each"></a>parallel_for_each 函式C++ （AMP）

跨計算網域執行函數。 如需詳細資訊，請參閱[ C++ AMP 總覽](../../../parallel/amp/cpp-amp-overview.md)。

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
要在其上執行平行計算的 `accelerator_view` 物件。

*_Compute_domain*<br/>
`extent` 物件，其中包含用於計算的資料。

*_Dim0*<br/>
`tiled_extent` 物件的維度。

*_Dim1*<br/>
`tiled_extent` 物件的維度。

*_Dim2*<br/>
`tiled_extent` 物件的維度。

*_Kernel*<br/>
Lambda 或函式物件，接受 "index\<類型的引數 _Rank >"，並執行平行計算。

*_Kernel_type*<br/>
Lambda 或仿函數。

*_Rank*<br/>
範圍的順位。

## <a name="tile_static_memory_fence"></a>tile_static_memory_fence

封鎖磚中所有線程的執行，直到完成所有未完成的 `tile_static` 記憶體存取為止。 這可確保 [執行緒] 磚中的其他執行緒可以看見 `tile_static` 的記憶體存取，而且該存取會依照程式循序執行。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>參數

*_Barrier*<br/>
Tile_barrier 物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

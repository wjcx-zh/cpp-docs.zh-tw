---
title: accelerator 類別
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 72a570ab28696730f835c42748a6ea12b865ca55
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855910"
---
# <a name="accelerator-class"></a>accelerator 類別

加速器是針對資料平行運算優化的硬體功能。 加速器可能是連接到 PCIe 匯流排的裝置（例如 GPU），或者它可能是在主要 CPU 上設定的擴充指令。

## <a name="syntax"></a>語法

```cpp
class accelerator;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[快速鍵對應函數](#ctor)|將 `accelerator` 類別的新執行個體初始化。|
|[~ 加速器的函式](#ctor)|終結 `accelerator` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[create_view](#create_view)|建立並傳回此快速鍵上的 `accelerator_view` 物件。|
|[get_all](#get_all)|傳回代表所有可用加速器的 `accelerator` 物件向量。|
|[get_auto_selection_view](#get_auto_selection_view)|傳回自動選取 `accelerator_view`。|
|[get_dedicated_memory](#get_dedicated_memory)|傳回 `accelerator`的專用記憶體（以 kb 為單位）。|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|傳回在此快速鍵上建立之緩衝區的預設[access_type](concurrency-namespace-enums-amp.md#access_type) 。|
|[get_default_view](#get_default_view)|傳回與 `accelerator`相關聯的預設 `accelerator_view` 物件。|
|[get_description](#get_description)|傳回 `accelerator` 裝置的簡短描述。|
|[get_device_path](#get_device_path)|傳回裝置的路徑。|
|[get_has_display](#get_has_display)|決定是否將 `accelerator` 附加至顯示。|
|[get_is_debug](#get_is_debug)|判斷 `accelerator` 是否已啟用 DEBUG 層以進行廣泛的錯誤報表。|
|[get_is_emulated](#get_is_emulated)|判斷是否模擬 `accelerator`。|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|判斷 `accelerator` 是否支援共用記憶體|
|[get_supports_double_precision](#get_supports_double_precision)|決定是否將 `accelerator` 附加至顯示。|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|判斷 `accelerator` 是否對雙精確度運算具有有限的支援。|
|[get_version](#get_version)|傳回 `accelerator`的版本。|
|[set_default](#set_default)|傳回預設快速鍵的路徑。|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|設定此 `accelerator`上的陣列和隱含記憶體配置的預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|比較這個 `accelerator` 物件與另一個，如果相同，則傳回**false** ;否則，會傳回**true**。|
|[operator=](#operator_eq)|將指定之 `accelerator` 物件的內容複寫到這個。|
|[operator==](#operator_eq_eq)|比較這個 `accelerator` 物件與另一個，如果相同，則傳回**true** ;否則，會傳回**false**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|取得 CPU `accelerator`的字串常數。|
|[dedicated_memory](#dedicated_memory)|取得 `accelerator`的專用記憶體（以 kb 為單位）。|
|[default_accelerator](#default_accelerator)|取得預設 `accelerator`的字串常數。|
|[default_cpu_access_type](#default_cpu_access_type)|取得或設定在此 `accelerator`上進行的陣列和隱含記憶體配置的預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)。|
|[default_view](#default_view)|取得與 `accelerator`相關聯的預設 `accelerator_view` 物件。|
|[description](#description)|取得 `accelerator` 裝置的簡短描述。|
|[device_path](#device_path)|取得裝置的路徑。|
|[direct3d_ref](#direct3d_ref)|取得 Direct3D 參考 `accelerator`的字串常數。|
|[direct3d_warp](#direct3d_warp)|取得 `accelerator` 物件的字串常數，您可以用來在使用 Streaming SIMD Extensions C++ （SSE）的多核心 cpu 上執行 AMP 程式碼。|
|[has_display](#has_display)|取得布林值，指出 `accelerator` 是否附加至顯示。|
|[is_debug](#is_debug)|指出 `accelerator` 是否已啟用 DEBUG 層以進行廣泛的錯誤報表。|
|[is_emulated](#is_emulated)|指出是否模擬 `accelerator`。|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|指出 `accelerator` 是否支援共用記憶體。|
|[supports_double_precision](#supports_double_precision)|指出快速鍵是否支援雙精確度數學運算。|
|[supports_limited_double_precision](#supports_limited_double_precision)|指出快速鍵對於雙精確度運算是否有有限的支援。|
|[version](#version)|取得 `accelerator` 的版本。|

## <a name="inheritance-hierarchy"></a>繼承階層

`accelerator`

## <a name="remarks"></a>備註

加速器是針對資料平行運算優化的硬體功能。 加速器通常是離散 GPU，但也可以是虛擬主機端實體（例如 DirectX REF 裝置）、彎曲（以 SSE 指示加速的 CPU 端裝置）或 CPU 本身。

您可以藉由列舉可用的裝置，或取得預設裝置、參照裝置或扭曲裝置，來建立 `accelerator` 物件。

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="dtor"></a></a> ~ 加速器

終結 `accelerator` 物件。

```cpp
~accelerator();
```

### <a name="return-value"></a>傳回值

## <a name="ctor"></a>加速器

初始化[快速鍵類別](accelerator-class.md)的新實例。

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>參數

*_Device_path*<br/>
實體裝置的路徑。

*_Other*<br/>
要複製的快速鍵。

## <a name="cpu_accelerator"></a>cpu_accelerator

取得 CPU 加速器的字串常數。

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a>create_view

使用指定的佇列模式，建立並傳回此快速鍵上的 `accelerator_view` 物件。 未指定佇列模式時，新的 `accelerator_view` 會使用[queuing_mode：： immediate](concurrency-namespace-enums-amp.md#queuing_mode)佇列模式。

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>參數

*qmode*<br/>
佇列模式。

### <a name="return-value"></a>傳回值

這個快速鍵上的新 `accelerator_view` 物件，使用指定的佇列模式。

## <a name="dedicated_memory"></a>dedicated_memory

取得 `accelerator`的專用記憶體（以 kb 為單位）。

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a>default_accelerator

取得預設 `accelerator`的字串常數。

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a>default_cpu_access_type

對此 `accelerator`進行的陣列和隱含記憶體配置的預設 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)。

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a>default_view

取得與 `accelerator`相關聯的預設快捷方式視圖。

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a>描述

取得 `accelerator` 裝置的簡短描述。

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a>device_path

取得快速鍵的路徑。 此路徑在系統上是唯一的。

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a>direct3d_ref

取得 Direct3D 參考加速器的字串常數。

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a>direct3d_warp

取得 `accelerator` 物件的字串常數，您可以用來在使用 Streaming SIMD Extensions （ C++ SSE）的多核心 cpu 上執行 AMP 程式碼。

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a>get_all

傳回代表所有可用加速器的 `accelerator` 物件向量。

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>傳回值

可用加速器的向量

## <a name="get_auto_selection_view"></a>get_auto_selection_view

傳回自動選取 accelerator_view，當指定為 parallel_for_each 目標時，會導致執行 parallel_for_each 核心的目標 accelerator_view 自動由執行時間選取。 針對所有其他用途，此方法所傳回的 accelerator_view 與預設快速鍵的預設 accelerator_view 相同

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>傳回值

自動選取 accelerator_view。

## <a name="get_dedicated_memory"></a>get_dedicated_memory

傳回 `accelerator`的專用記憶體（以 kb 為單位）。

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>傳回值

`accelerator`的專用記憶體（以 kb 為單位）。

## <a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

取得在此加速器上建立之緩衝區的預設 cpu access_type

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>傳回值

在此加速器上建立之緩衝區的預設 cpu access_type。

## <a name="get_default_view"></a>get_default_view

傳回與 `accelerator`相關聯的預設 `accelerator_view` 物件。

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>傳回值

與 `accelerator`相關聯的預設 `accelerator_view` 物件。

## <a name="get_description"></a>get_description

傳回 `accelerator` 裝置的簡短描述。

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>傳回值

`accelerator` 裝置的簡短描述。

## <a name="get_device_path"></a>get_device_path

傳回快速鍵的路徑。 此路徑在系統上是唯一的。

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>傳回值

全系統的唯一裝置實例路徑。

## <a name="get_has_display"></a>get_has_display

傳回布林值，指出 `accelerator` 是否可以輸出到顯示器。

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>傳回值

如果 `accelerator` 可以輸出到顯示，則為**true** ;否則**為 false**。

## <a name="get_is_debug"></a>get_is_debug

判斷 `accelerator` 是否已啟用 DEBUG 層以進行廣泛的錯誤報表。

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>傳回值

如果 `accelerator` 已啟用 DEBUG 層來進行廣泛的錯誤報表，則**為 true** 。 否則為 **false**。

## <a name="get_is_emulated"></a>get_is_emulated

判斷是否模擬 `accelerator`。

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>傳回值

如果 `accelerator` 是模擬的，**則為 true** 。 否則為 **false**。

## <a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

傳回布林值，指出加速器是否支援加速器和 CPU 可存取的記憶體。

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>傳回值

如果加速器支援 CPU 共用記憶體，則**為 true** ;否則**為 false**。

## <a name="get_supports_double_precision"></a>get_supports_double_precision

傳回布林值，指出快速鍵是否支援雙精確度運算，包括融合的乘法加法（FMA）、除法、倒數和**int**與**double**之間的轉換

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>傳回值

如果快速鍵支援雙精確度運算，則**為 true** ;否則**為 false**。

## <a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

傳回布林值，指出快速鍵是否對雙精確度運算具有有限的支援。 如果加速器只有有限的支援，則不支援在**int**與**double**之間進行已融合的加法（FMA）、除法、互惠和轉換。

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>傳回值

如果快速鍵對雙精確度運算的支援有限，則為**true** ;否則**為 false**。

## <a name="get_version"></a>get_version

傳回 `accelerator`的版本。

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>傳回值

`accelerator` 的版本。

## <a name="has_display"></a>has_display

取得布林值，指出 `accelerator` 是否可以輸出到顯示器。

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a>is_debug

取得布林值，指出 `accelerator` 是否已啟用 DEBUG 層來進行大量錯誤報表。

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a>is_emulated

取得布林值，指出是否模擬 `accelerator`。

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator_neq"></a>operator！ =

比較這個 `accelerator` 物件與另一個，如果相同，則傳回**false** ;否則，會傳回**true**。

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>參數

*_Other*<br/>
要與這個比較的 `accelerator` 物件。

### <a name="return-value"></a>傳回值

如果兩個 `accelerator` 物件相同，則為**false** ;否則**為 true**。

## <a name="operator_eq"></a>operator =

將指定之 `accelerator` 物件的內容複寫到這個。

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源 `accelerator` 物件。

### <a name="return-value"></a>傳回值

這個 `accelerator` 物件的參考。

## <a name="operator_eq_eq"></a>operator = =

比較這個 `accelerator` 物件與另一個，如果相同，則傳回**true** ;否則，會傳回**false**。

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>參數

*_Other*<br/>
要與這個比較的 `accelerator` 物件。

### <a name="return-value"></a>傳回值

如果其他 `accelerator` 物件與這個 `accelerator` 物件相同，則為**true** ;否則**為 false**。

## <a name="set_default"></a>set_default

設定預設快速鍵，以用於隱含使用預設快速鍵的任何作業。 只有當執行時間選取的預設快速鍵尚未用於隱含使用預設加速器的作業時，這個方法才會成功

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>參數

*_Path*<br/>
快速鍵的路徑。

### <a name="return-value"></a>傳回值

如果在設定預設快速鍵時呼叫成功，**則為 true** 。 否則為 **false**。

## <a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

設定在此加速器上建立之陣列的預設 cpu access_type，或是在此加速器上存取 array_views 的一部分，為隱含的記憶體配置。 只有在先前的呼叫此方法未覆寫快速鍵的 default_cpu_access_type，而且尚未使用為此快速鍵所選取 default_cpu_access_type 的執行時間尚未用於配置陣列或的時，這個方法才會成功。支援在此加速器上存取之 array_view 的隱含記憶體配置。

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>參數

*_Default_cpu_access_type*<br/>
要在此加速器上用於陣列/array_view 記憶體配置的預設 cpu access_type。

### <a name="return-value"></a>傳回值

布林值，指出是否已成功設定加速器的預設 cpu access_type。

## <a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

取得布林值，指出 `accelerator` 是否支援共用記憶體。

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a>supports_double_precision

取得布林值，指出快速鍵是否支援雙精確度數學運算。

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a>supports_limited_double_precision

取得布林值，指出快速鍵是否對雙精確度運算具有有限的支援。 如果加速器只有有限的支援，則不支援在 `int` 和 `double` 之間進行融合的乘法加（FMA）、除法、倒數和轉換。

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>版本

取得 `accelerator` 的版本。

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

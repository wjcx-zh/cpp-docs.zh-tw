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
ms.openlocfilehash: 5cf3cbb0cbff10deb029e81945f63921495bd0de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522264"
---
# <a name="accelerator-class"></a>accelerator 類別

加速器是適用於資料平行計算的硬體功能。 加速器可能是附加至 PCIe 匯流排 （例如 GPU) 的裝置，或可能是主要 CPU 上設定的擴充的指令。

## <a name="syntax"></a>語法

```
class accelerator;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[accelerator 建構函式](#ctor)|初始化 `accelerator` 類別的新執行個體。|
|[~ accelerator 解構函式](#ctor)|終結`accelerator`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[create_view](#create_view)|建立並傳回`accelerator_view`此加速器上的物件。|
|[get_all](#get_all)|傳回向量的位元`accelerator`物件，代表所有可用的加速器。|
|[get_auto_selection_view](#get_auto_selection_view)|傳回自動選取`accelerator_view`。|
|[get_dedicated_memory](#get_dedicated_memory)|傳回的專屬的記憶體`accelerator`，以 kb 為單位。|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|傳回的預設[access_type](concurrency-namespace-enums-amp.md#access_type)建立於此加速器的緩衝區。|
|[get_default_view](#get_default_view)|傳回的預設`accelerator_view`相關聯的物件`accelerator`。|
|[get_description](#get_description)|傳回的簡短描述`accelerator`裝置。|
|[get_device_path](#get_device_path)|傳回裝置的路徑。|
|[get_has_display](#get_has_display)|決定是否`accelerator`附加至顯示器。|
|[get_is_debug](#get_is_debug)|決定是否`accelerator`有擴充錯誤報告啟用偵錯層級。|
|[get_is_emulated](#get_is_emulated)|決定是否`accelerator`模擬。|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|決定是否`accelerator`支援共用記憶體|
|[get_supports_double_precision](#get_supports_double_precision)|決定是否`accelerator`附加至顯示器。|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|決定是否`accelerator`有限雙精確度運算的支援。|
|[get_version](#get_version)|傳回的版本`accelerator`。|
|[set_default](#set_default)|傳回預設加速器的路徑。|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|設定的預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)之陣列與隱含記憶體配置，這對`accelerator`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|比較這個`accelerator`與另一個物件，然後傳回**false**它們是相同的; 否則會傳回**true**。|
|[operator=](#operator_eq)|將指定的內容複製`accelerator`如下的物件。|
|[operator==](#operator_eq_eq)|比較這個`accelerator`與另一個物件，然後傳回 **，則為 true**它們是相同的; 否則會傳回**false**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|取得 cpu 的常數字串`accelerator`。|
|[dedicated_memory](#dedicated_memory)|取得的專屬的記憶體`accelerator`，以 kb 為單位。|
|[default_accelerator](#default_accelerator)|取得預設的常數字串`accelerator`。|
|[default_cpu_access_type](#default_cpu_access_type)|取得或設定的預設 CPU [access_type](concurrency-namespace-enums-amp.md#access_type)之陣列與隱含記憶體配置，這對`accelerator`。|
|[default_view](#default_view)|取得預設值`accelerator_view`相關聯的物件`accelerator`。|
|[description](#description)|取得的簡短描述`accelerator`裝置。|
|[device_path](#device_path)|取得裝置的路徑。|
|[direct3d_ref](#direct3d_ref)|取得 Direct3D 參考的常數字串`accelerator`。|
|[direct3d_warp](#direct3d_warp)|取得的字串常數`accelerator`物件，您可以用來使用 Streaming SIMD Extensions (SSE) 的多核心 Cpu 上執行 c + + AMP 程式碼。|
|[has_display](#has_display)|取得布林值，指出是否`accelerator`附加至顯示器。|
|[is_debug](#is_debug)|指出是否`accelerator`有擴充錯誤報告啟用偵錯層級。|
|[is_emulated](#is_emulated)|指出是否`accelerator`模擬。|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|指出是否`accelerator`支援共用記憶體。|
|[supports_double_precision](#supports_double_precision)|表示加速器是否支援雙精確度數學運算。|
|[supports_limited_double_precision](#supports_limited_double_precision)|指出是否加速器是否限制了雙精確度運算的支援。|
|[version](#version)|取得版本`accelerator`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`accelerator`

## <a name="remarks"></a>備註

加速器是適用於資料平行計算的硬體功能。 加速器通常是離散的 GPU，但它也可以是虛擬主應用程式端實體，例如 DirectX REF 裝置、 WARP （透過 SSE 指令加速度的 CPU 端裝置） 或 CPU 本身。

您可以建構`accelerator`物件列舉可用的裝置，或藉由取得預設裝置、 參考裝置或 WARP 裝置。

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行

##  <a name="dtor"></a> </a> ~ accelerator

終結`accelerator`物件。

```
~accelerator();
```

### <a name="return-value"></a>傳回值

##  <a name="ctor"></a> 加速器

初始化的新執行個體[加速器類別](accelerator-class.md)。

```
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>參數

*_Device_path*<br/>
實體裝置的路徑。

*_Other*<br/>
要複製的加速器。

##  <a name="cpu_accelerator"></a> cpu_accelerator

取得 CPU 加速器常數字串。

```
static const wchar_t cpu_accelerator[];
```

##  <a name="create_view"></a> create_view

建立並傳回`accelerator_view`於此加速器，使用指定的佇列模式的物件。 未指定的佇列模式時，新`accelerator_view`會使用[queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode)佇列模式。

```
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>參數

*qmode*<br/>
佇列的模式。

### <a name="return-value"></a>傳回值

新`accelerator_view`於此加速器，使用指定的佇列模式的物件。

##  <a name="dedicated_memory"></a> dedicated_memory

取得的專屬的記憶體`accelerator`，以 kb 為單位。

```
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

##  <a name="default_accelerator"></a> default_accelerator

取得預設的常數字串`accelerator`。

```
static const wchar_t default_accelerator[];
```

##  <a name="default_cpu_access_type"></a> default_cpu_access_type

的預設 cpu [access_type](concurrency-namespace-enums-amp.md#access_type)之陣列與隱含記憶體配置，這對`accelerator`。

```
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

##  <a name="default_view"></a> default_view

取得相關聯的預設加速器檢視`accelerator`。

```
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

##  <a name="description"></a> 描述

取得的簡短描述`accelerator`裝置。

```
__declspec(property(get= get_description)) std::wstring description;
```

##  <a name="device_path"></a> device_path

取得加速器的路徑。 路徑是唯一的系統上。

```
__declspec(property(get= get_device_path)) std::wstring device_path;
```

##  <a name="direct3d_ref"></a> direct3d_ref

取得 Direct3D 參考加速器常數字串。

```
static const wchar_t direct3d_ref[];
```

##  <a name="direct3d_warp"></a> direct3d_warp

取得的字串常數`accelerator`物件，您可以用來使用 Streaming SIMD Extensions (SSE) 的多核心 Cpu 上執行您的 c + + AMP 程式碼。

```
static const wchar_t direct3d_warp[];
```

##  <a name="get_all"></a> get_all

傳回向量的位元`accelerator`物件，代表所有可用的加速器。

```
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>傳回值

可用的加速器的向量

##  <a name="get_auto_selection_view"></a> get_auto_selection_view

傳回自動選取 accelerator_view，當指定為 parallel_for_each 目標結果中的執行執行階段會自動選取的 parallel_for_each kernel 而於目標 accelerator_view。 對於所有其他目的，這個方法所傳回的 accelerator_view 是預設加速器的預設 accelerator_view 相同

```
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>傳回值

自動選取 accelerator_view。

##  <a name="get_dedicated_memory"></a> get_dedicated_memory

傳回的專屬的記憶體`accelerator`，以 kb 為單位。

```
size_t get_dedicated_memory() const;

```

### <a name="return-value"></a>傳回值

專屬的記憶體`accelerator`，以 kb 為單位。

##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type

取得建立於此加速器之緩衝區的預設 cpu access_type

```
access_type get_default_cpu_access_type() const;

```

### <a name="return-value"></a>傳回值

在此加速器上建立的緩衝區預設 cpu access_type。

##  <a name="get_default_view"></a> get_default_view

傳回的預設`accelerator_view`相關聯的物件`accelerator`。

```
accelerator_view get_default_view() const;

```

### <a name="return-value"></a>傳回值

預設值`accelerator_view`相關聯的物件`accelerator`。

##  <a name="get_description"></a> get_description

傳回的簡短描述`accelerator`裝置。

```
std::wstring get_description() const;

```

### <a name="return-value"></a>傳回值

簡短描述`accelerator`裝置。

##  <a name="get_device_path"></a> get_device_path

傳回這個加速器的路徑。 路徑是唯一的系統上。

```
std::wstring get_device_path() const;

```

### <a name="return-value"></a>傳回值

全系統的唯一裝置執行個體路徑。

##  <a name="get_has_display"></a> get_has_display

傳回布林值，指出是否`accelerator`可以輸出至顯示器。

```
bool get_has_display() const;

```

### <a name="return-value"></a>傳回值

**真**如果`accelerator`可以輸出至顯示器，否則**false**。

##  <a name="get_is_debug"></a> get_is_debug

決定是否`accelerator`有擴充錯誤報告啟用偵錯層級。

```
bool get_is_debug() const;

```

### <a name="return-value"></a>傳回值

**真**如果`accelerator`有擴充錯誤報告啟用偵錯層級。 否則，請**false**。

##  <a name="get_is_emulated"></a> get_is_emulated

決定是否`accelerator`模擬。

```
bool get_is_emulated() const;

```

### <a name="return-value"></a>傳回值

**真**如果`accelerator`模擬。 否則，請**false**。

##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory

傳回布林值，指出加速器是否支援皆可存取的加速器和 CPU 的記憶體。

```
bool get_supports_cpu_shared_memory() const;

```

### <a name="return-value"></a>傳回值

**true**如果加速器支援 CPU 共用記憶體中; 否則**false**。

##  <a name="get_supports_double_precision"></a> get_supports_double_precision

傳回布林值，表示加速器是否支援雙精確度浮點，包括融合乘加法 (FMA)，除法，倒數，以及之間的轉換**int**和**double**

```
bool get_supports_double_precision() const;

```

### <a name="return-value"></a>傳回值

**真**如果加速器支援雙精確度數學; 否則**false**。

##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision

傳回布林值，指出是否加速器是否限制了雙精確度運算的支援。 加速器是否只有有限的支援，然後融合乘加法 (FMA)，除法，倒數，以及之間的轉換**int**並**double**不支援。

```
bool get_supports_limited_double_precision() const;

```

### <a name="return-value"></a>傳回值

**真**如果加速器是否限制了雙精確度數學; 的支援，否則為**false**。

##  <a name="get_version"></a> get_version

傳回的版本`accelerator`。

```
unsigned int get_version() const;

```

### <a name="return-value"></a>傳回值

新版`accelerator`。

##  <a name="has_display"></a> has_display

取得布林值，指出是否`accelerator`可以輸出至顯示器。

```
__declspec(property(get= get_has_display)) bool has_display;
```

##  <a name="is_debug"></a> is_debug

取得布林值，指出是否`accelerator`有擴充錯誤報告啟用偵錯層級。

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="is_emulated"></a> is_emulated

取得布林值，指出是否`accelerator`模擬。

```
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

##  <a name="operator_neq"></a> 運算子 ！ =

比較這個`accelerator`與另一個物件，然後傳回**false**它們是相同的; 否則會傳回**true**。

```
bool operator!= (const accelerator& _Other) const;

```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**false**如果兩個`accelerator`物件是否相同，否則 **，則為 true**。

##  <a name="operator_eq"></a> 運算子 =

將指定的內容複製`accelerator`如下的物件。

```
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator`從複製的物件。

### <a name="return-value"></a>傳回值

此參考`accelerator`物件。

##  <a name="operator_eq_eq"></a> 運算子 = =

比較這個`accelerator`與另一個物件，然後傳回 **，則為 true**它們是相同的; 否則會傳回**false**。

```
bool operator== (const accelerator& _Other) const;

```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**則為 true**如果另`accelerator`物件是否與此相同`accelerator`物件; 否則**false**。

##  <a name="set_default"></a> set_default

設定要用於任何作業，會隱含地使用預設加速器的預設加速器。 這個方法才會成功執行階段選取的預設加速器不已經使用中的作業，會隱含地使用預設加速器

```
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>參數

*路徑 （_p)*<br/>
要在加速器的路徑。

### <a name="return-value"></a>傳回值

**true**如果呼叫成功設定預設加速器。 否則，請**false**。

##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type

設定於此加速器存取之 array_views 一部分的陣列建立於此加速器或隱含記憶體配置的預設 cpu access_type。 這個方法才會成功如果加速器的 default_cpu_access_type 未尚未由先前呼叫這個方法的覆寫，而且這個加速器的執行階段選取 default_cpu_access_type 未具有尚未使用或用於配置陣列支援於此加速器存取之 array_view 的隱含記憶體配置。

```
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>參數

*_Default_cpu_access_type*<br/>
要用於 array/array_view 記憶體配置，在此加速器上預設 cpu access_type。

### <a name="return-value"></a>傳回值

布林值，指出是否成功設定加速器的預設 cpu access_type。

##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory

取得布林值，指出是否`accelerator`支援共用記憶體。

```
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

##  <a name="supports_double_precision"></a> supports_double_precision

取得布林值，表示加速器是否支援雙精確度數學運算。

```
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision

取得布林值，指出是否加速器是否限制了雙精確度運算的支援。 如果加速器都只有有限的支援，然後融合乘加法 (FMA)，除法，倒數，以及之間的轉換`int`和`double`不支援。

```
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

##  <a name="version"></a> 版本

取得版本`accelerator`。

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="dtor"></a> </a> ~ accelerator_view

終結[accelerator_view](accelerator-view-class.md)物件。

```
~accelerator_view();
```

### <a name="return-value"></a>傳回值

##  <a name="accelerator"></a> 加速器

取得`accelerator`物件[accelerator_view](accelerator-view-class.md)物件。

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

##  <a name="ctor"></a> accelerator_view

初始化的新執行個體[accelerator_view](accelerator-view-class.md)藉由複製現有的類別`accelerator_view`物件。

```
accelerator_view(const accelerator_view& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`来複製的物件。

##  <a name="create_marker"></a> create_marker

傳回追蹤的所有目前提交至此的命令完成的未來`accelerator_view`物件。

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>傳回值

若要追蹤的所有目前提交至此的命令完成的未來`accelerator_view`物件。

##  <a name="flush"></a> 排清

提交所有暫止命令排入佇列[accelerator_view](accelerator-view-class.md)至加速器以執行的物件。

```
void flush();
```

### <a name="return-value"></a>傳回值

傳回 `void`。

##  <a name="get_accelerator"></a> get_accelerator

傳回`accelerator`物件[accelerator_view](accelerator-view-class.md)物件。

```
accelerator get_accelerator() const;

```

### <a name="return-value"></a>傳回值

`accelerator`物件`accelerator_view`物件。

##  <a name="get_is_auto_selection"></a> get_is_auto_selection

傳回布林值，指出是否執行階段會自動選取適當的加速器時在 accelerator_view 傳遞至[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。

```
bool get_is_auto_selection() const;

```

### <a name="return-value"></a>傳回值

**真**如果執行階段會自動選取適當的加速器;，否則為**false**。

##  <a name="get_is_debug"></a> get_is_debug

傳回布林值，指出是否[accelerator_view](accelerator-view-class.md)物件具有擴充錯誤報告啟用偵錯層級。

```
bool get_is_debug() const;

```

### <a name="return-value"></a>傳回值

布林值，指出是否`accelerator_view`物件具有擴充錯誤報告啟用偵錯層級。

##  <a name="get_queuing_mode"></a> get_queuing_mode

傳回的佇列模式[accelerator_view](accelerator-view-class.md)物件。

```
queuing_mode get_queuing_mode() const;

```

### <a name="return-value"></a>傳回值

佇列模式`accelerator_view`物件。

##  <a name="get_version"></a> get_version

傳回的版本[accelerator_view](accelerator-view-class.md)。

```
unsigned int get_version() const;

```

### <a name="return-value"></a>傳回值

新版`accelerator_view`。

##  <a name="is_auto_selection"></a> is_auto_selection

取得布林值，指出是否執行階段會自動選取適當的加速器時在 accelerator_view 傳遞至[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)。

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

##  <a name="is_debug"></a> is_debug

取得布林值，指出是否[accelerator_view](accelerator-view-class.md)物件具有擴充錯誤報告啟用偵錯層級。

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="operator_neq"></a> 運算子 ！ =

比較這個[accelerator_view](accelerator-view-class.md)與另一個物件，然後傳回`false`它們是相同的; 否則會傳回`true`。

```
bool operator!= (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**false**兩個物件是否相同，否則 **，則為 true**。

##  <a name="operator_eq"></a> 運算子 =

將指定的內容複製[accelerator_view](accelerator-view-class.md)到這個物件。

```
accelerator_view& operator= (const accelerator_view& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`從複製的物件。

### <a name="return-value"></a>傳回值

已修改的參考`accelerator_view`物件。

##  <a name="operator_eq_eq"></a> 運算子 = =

比較這個[accelerator_view](accelerator-view-class.md)與另一個物件，然後傳回 **，則為 true**相同; 否則會傳回**false**。

```
bool operator== (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**true**兩個物件是否相同，否則**false**。

##  <a name="queuing_mode"></a> queuing_mode

取得的佇列模式[accelerator_view](accelerator-view-class.md)物件。

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

##  <a name="version"></a> 版本

取得版本[accelerator_view](accelerator-view-class.md)。

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="wait"></a> 等候

等候所有命令提交給[accelerator_view](accelerator-view-class.md)完成的物件。

```
void wait();
```

### <a name="return-value"></a>傳回值

傳回 `void`。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

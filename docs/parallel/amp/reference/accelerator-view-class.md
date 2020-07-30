---
title: accelerator_view 類別
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 0020acfda7b506bf9f0547b9daedff34d80204f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182755"
---
# <a name="accelerator_view-class"></a>accelerator_view 類別

表示 C++ AMP 資料平行加速器上的虛擬裝置抽象概念。

## <a name="syntax"></a>語法

```cpp
class accelerator_view;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[accelerator_view 的構造函式](#ctor)|初始化 `accelerator_view` 類別的新執行個體。|
|[~ accelerator_view 的析構函式](#dtor)|終結 `accelerator_view` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[create_marker](#create_marker)|會傳回未來，追蹤到目前為止提交到此物件的所有命令是否完成 `accelerator_view` 。|
|[刷](#flush)|將所有已排入物件佇列的暫止命令提交 `accelerator_view` 至加速器執行。|
|[get_accelerator](#get_accelerator)|傳回 `accelerator` 物件的 `accelerator_view` 物件。|
|[get_is_auto_selection](#get_is_auto_selection)|傳回布林值，指出當 `accelerator_view` 物件傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時，執行時間是否會自動選取適當的快速鍵。|
|[get_is_debug](#get_is_debug)|傳回布林值，指出 `accelerator_view` 物件是否已啟用 DEBUG 層來進行大量錯誤報表。|
|[get_queuing_mode](#get_queuing_mode)|傳回物件的佇列模式 `accelerator_view` 。|
|[get_version](#get_version)|傳回的版本 `accelerator_view` 。|
|[等候](#wait)|等候所有提交給物件的命令 `accelerator_view` 完成。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[operator！ =](#operator_neq)|比較此 `accelerator_view` 物件與另一個，並在 **`false`** 兩者相同的情況下傳回; 否則會傳回 **`true`** 。|
|[operator =](#operator_eq)|將指定之物件的內容複寫 `accelerator_view` 到這個。|
|[operator = =](#operator_eq_eq)|比較此 `accelerator_view` 物件與另一個，並在 **`true`** 兩者相同的情況下傳回; 否則會傳回 **`false`** 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[加速器](#accelerator)|取得 `accelerator_view` 物件的 `accelerator` 物件。|
|[is_auto_selection](#is_auto_selection)|取得布林值，指出當 `accelerator_view` 物件傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時，執行時間是否會自動選取適當的快速鍵。|
|[is_debug](#is_debug)|取得布林值，指出 `accelerator_view` 物件是否已啟用 DEBUG 層來進行大量錯誤報表。|
|[queuing_mode](#queuing_mode)|取得物件的佇列模式 `accelerator_view` 。|
|[version](#version)|取得加速器的版本。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`accelerator_view`

### <a name="remarks"></a>備註

`accelerator_view`物件代表快速鍵的邏輯獨立視圖。 單一實體計算裝置可以有許多邏輯、隔離的 `accelerator_view` 物件。 每個加速器都有預設 `accelerator_view` 物件。 `accelerator_view`可以建立其他物件。

實體裝置可以在許多用戶端執行緒之間共用。 用戶端執行緒可以合作使用相同 `accelerator_view` 的加速器物件，或每個用戶端都可以透過獨立物件與計算裝置進行通訊， `accelerator_view` 以與其他用戶端執行緒隔離。

`accelerator_view`物件可以有兩個[queuing_mode 列舉](concurrency-namespace-enums-amp.md#queuing_mode)狀態的其中一個。 如果佇列模式為 `immediate` ，則像和等命令 `copy` 會在 `parallel_for_each` 傳回給呼叫者時立即傳送至對應的加速器裝置。 如果佇列模式為 `deferred` ，這類命令會在對應至物件的命令佇列上排入佇列 `accelerator_view` 。 在呼叫之前，命令實際上不會傳送至裝置 `flush()` 。

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="accelerator"></a><a name="accelerator"></a>加速器

取得 accelerator_view 物件的快速鍵物件。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

藉由複製現有的物件，初始化 accelerator_view 類別的新實例 `accelerator_view` 。

### <a name="syntax"></a>語法

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>參數

*另一方面*<br/>
要複製的 `accelerator_view` 物件。

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

會傳回未來，追蹤到目前為止提交到此物件的所有命令是否完成 `accelerator_view` 。

### <a name="syntax"></a>語法

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>傳回值

未來追蹤到目前為止提交到此物件的所有命令是否完成 `accelerator_view` 。

## <a name="flush"></a>flush

將所有已排入佇列至 accelerator_view 物件的暫止命令提交至加速器進行執行。

### <a name="syntax"></a>語法

```cpp
void flush();
```

### <a name="return-value"></a>傳回值

傳回 **`void`** 。

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

傳回 accelerator_view 物件的快速鍵物件。

### <a name="syntax"></a>語法

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>傳回值

Accelerator_view 物件的快速鍵物件。

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

傳回布林值，指出當 accelerator_view 傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時，執行時間是否會自動選取適當的快速鍵。

### <a name="syntax"></a>語法

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果執行時間會自動選取適當的加速器，則為，否則為 **`false`** 。

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

傳回布林值，指出 accelerator_view 物件是否已啟用 DEBUG 層來進行大量錯誤報表。

### <a name="syntax"></a>語法

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>傳回值

布林值，指出 `accelerator_view` 物件是否已啟用 DEBUG 層來進行大量錯誤報表。

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

傳回 accelerator_view 物件的佇列模式。

### <a name="syntax"></a>語法

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>傳回值

物件的佇列模式 `accelerator_view` 。

## <a name="get_version"></a><a name="get_version"></a>get_version

傳回 accelerator_view 的版本。

### <a name="syntax"></a>語法

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>傳回值

`accelerator_view` 的版本。

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

取得布林值，指出當 accelerator_view 傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時，執行時間是否會自動選取適當的快速鍵。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

取得布林值，該值會指出 accelerator_view 物件是否已啟用 DEBUG 層以提供更詳細的錯誤報告。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>operator！ =

比較這個 accelerator_view 物件與另一個， **`false`** 如果相同，則傳回，否則傳回 **`true`** 。

### <a name="syntax"></a>語法

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**`false`** 如果兩個物件相同，則為，否則為 **`true`** 。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將指定 accelerator_view 物件的內容複寫到這個。

### <a name="syntax"></a>語法

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>參數

*另一方面*<br/>
`accelerator_view`要複製的物件。

### <a name="return-value"></a>傳回值

已修改之物件的參考 `accelerator_view` 。

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

比較這個 accelerator_view 物件與另一個， **`true`** 如果相同，則傳回，否則傳回 **`false`** 。

### <a name="syntax"></a>語法

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果兩個物件相同，則為，否則為 **`false`** 。

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

取得 accelerator_view 物件的佇列模式。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

取得 accelerator_view 的版本。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

等待提交至 accelerator_view 物件的所有命令完成。

### <a name="syntax"></a>語法

```cpp
void wait();
```

### <a name="return-value"></a>傳回值

傳回 **`void`** 。

### <a name="remarks"></a>備註

如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)為 `immediate` ，則這個方法會立即傳回，而不會封鎖。

## <a name="accelerator_view"></a><a name="dtor"></a>~ accelerator_view

終結 accelerator_view 物件。

### <a name="syntax"></a>語法

```cpp
~accelerator_view();
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間（C++ AMP）](concurrency-namespace-cpp-amp.md)

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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370894"
---
# <a name="accelerator_view-class"></a>accelerator_view 類別

表示 C++ AMP 資料並行加速器上的虛擬設備抽象。

## <a name="syntax"></a>語法

```cpp
class accelerator_view;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[accelerator_view建構函數](#ctor)|將 `accelerator_view` 類別的新執行個體初始化。|
|[*accelerator_view析構圖](#dtor)|銷毀`accelerator_view`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[create_marker](#create_marker)|返回一個未來,以跟蹤到目前為止提交給此`accelerator_view`物件的所有命令的完成情況。|
|[沖洗](#flush)|將所有排隊到物件等待`accelerator_view`執行的掛起命令提交到加速器執行。|
|[get_accelerator](#get_accelerator)|傳回 `accelerator` 物件的 `accelerator_view` 物件。|
|[get_is_auto_selection](#get_is_auto_selection)|返回一個布爾值,指示當`accelerator_view`物件傳遞給[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時,運行時是否將自動選擇適當的快速鍵。|
|[get_is_debug](#get_is_debug)|返回一個布爾值,指示`accelerator_view`物件是否啟用了 DEBUG 層以進行大量錯誤報告。|
|[get_queuing_mode](#get_queuing_mode)|返回`accelerator_view`物件的排隊模式。|
|[get_version](#get_version)|傳回的`accelerator_view`版本 。|
|[等](#wait)|等待提交到`accelerator_view`物件的所有命令完成。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[操作員!](#operator_neq)|將此`accelerator_view`物件與另一個對象進行比較,如果物件相同,則返回**false;** 否則,傳回**true**。|
|[運算子*](#operator_eq)|將指定`accelerator_view`物件的內容複製到此物件中。|
|[運算子*](#operator_eq_eq)|將此`accelerator_view`物件與另一個對象進行比較,如果物件相同,則返回**true;** 否則,傳回**false**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[加速器](#accelerator)|取得 `accelerator_view` 物件的 `accelerator` 物件。|
|[is_auto_selection](#is_auto_selection)|獲取布爾值,指示當`accelerator_view`物件傳遞到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時,運行時是否將自動選擇適當的加速器。|
|[is_debug](#is_debug)|獲取布林值,`accelerator_view`指示 物件是否已啟用 DEBUG 層以進行大量錯誤報告。|
|[queuing_mode](#queuing_mode)|獲取`accelerator_view`對象的排隊模式。|
|[version](#version)|獲取加速器的版本。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`accelerator_view`

### <a name="remarks"></a>備註

物件`accelerator_view`表示加速器的邏輯隔離視圖。 單個物理計算設備可以具有許多邏輯隔離`accelerator_view`物件。 每個加速器都有一個`accelerator_view`默認物件。 可以`accelerator_view`創建其他物件。

物理設備可以在許多用戶端線程之間共用。 用戶端線程可以協同使用加速器的同一`accelerator_view`物件,或者每個用戶端可以`accelerator_view`通過獨立 物件與計算設備通信,以便與其他用戶端線程隔離。

物件`accelerator_view`可以具有兩[個queuing_mode枚舉](concurrency-namespace-enums-amp.md#queuing_mode)狀態之一。 如果佇列模式為`immediate`,則`copy`命令`parallel_for_each`, 如和的命令在返回調用方後立即發送到相應的加速器設備。 如果排隊模式為`deferred`,則此類命令在對應`accelerator_view`於 物件的命令佇列上排隊。 在呼叫命令之前`flush()`,實際上不會將命令發送到設備。

## <a name="requirements"></a>需求

**標題:** amprt.h

**命名空間：** 並行

## <a name="accelerator"></a><a name="accelerator"></a>加速器

獲取accelerator_view物件的快速鍵物件。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

通過複製現有`accelerator_view`對象來初始化accelerator_view類的新實例。

### <a name="syntax"></a>語法

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>參數

*其他*<br/>
要複製的 `accelerator_view` 物件。

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

返回一個未來,以跟蹤到目前為止提交給此`accelerator_view`物件的所有命令的完成情況。

### <a name="syntax"></a>語法

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>傳回值

跟蹤到目前為止提交給此`accelerator_view`物件的所有命令的完成情況。

## <a name="flush"></a>flush

將所有排隊到accelerator_view物件等待執行的命令提交到加速器執行。

### <a name="syntax"></a>語法

```cpp
void flush();
```

### <a name="return-value"></a>傳回值

傳回 `void`。

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

返回accelerator_view物件的快速鍵物件。

### <a name="syntax"></a>語法

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>傳回值

accelerator_view物件的快捷鍵物件。

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

返回一個布爾值,指示當accelerator_view傳遞到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時,運行時是否將自動選擇適當的加速器。

### <a name="syntax"></a>語法

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>傳回值

如果執行時將自動選擇適當的加速器,**則為 true;** 否則,**假**。

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

返回一個布爾值,指示accelerator_view物件是否已啟用 DEBUG 層以進行大量錯誤報告。

### <a name="syntax"></a>語法

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>傳回值

一個布爾值,指示`accelerator_view`物件是否啟用了 DEBUG 層以進行大量錯誤報告。

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

返回accelerator_view物件的排隊模式。

### <a name="syntax"></a>語法

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>傳回值

`accelerator_view`對象的排隊模式。

## <a name="get_version"></a><a name="get_version"></a>get_version

返回accelerator_view的版本。

### <a name="syntax"></a>語法

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>傳回值

`accelerator_view` 的版本。

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

獲取布爾值,指示當accelerator_view傳遞到[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)時,運行時是否將自動選擇適當的加速器。

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

## <a name="operator"></a><a name="operator_neq"></a>操作員!

將此accelerator_view物件與另一個對象進行比較,如果物件相同,則返回**false;** 否則,傳回**true**。

### <a name="syntax"></a>語法

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
要`accelerator_view`與此比較的物件。

### <a name="return-value"></a>傳回值

如果兩個物件相同,**則為 false;** 否則,**真**。

## <a name="operator"></a><a name="operator_eq"></a>運算子*

將指定accelerator_view物件的內容複製到此物件中。

### <a name="syntax"></a>語法

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>參數

*其他*<br/>
要`accelerator_view`複製的物件。

### <a name="return-value"></a>傳回值

對修改`accelerator_view`物件的引用。

## <a name="operator"></a><a name="operator_eq_eq"></a>運算子*

將此accelerator_view物件與另一個對象進行比較,如果物件相同,則返回**true;** 否則,傳回**false**。

### <a name="syntax"></a>語法

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
要`accelerator_view`與此比較的物件。

### <a name="return-value"></a>傳回值

如果兩個物件相同,**則為 true;** 否則,**假**。

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

獲取accelerator_view對象的排隊模式。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

獲取accelerator_view的版本。

### <a name="syntax"></a>語法

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

等待提交到物件accelerator_view的所有命令完成。

### <a name="syntax"></a>語法

```cpp
void wait();
```

### <a name="return-value"></a>傳回值

傳回 `void`。

### <a name="remarks"></a>備註

如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)queuing_mode`immediate`為 ,則此方法將立即返回而不阻塞。

## <a name="accelerator_view"></a><a name="dtor"></a>*accelerator_view

銷毀accelerator_view物件。

### <a name="syntax"></a>語法

```cpp
~accelerator_view();
```

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)

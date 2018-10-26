---
title: accelerator_view 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b556a86506e3aae73f7ac4e1ac961b539364d6db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053557"
---
# <a name="acceleratorview-class"></a>accelerator_view 類別

表示在 c + + AMP 資料平行加速器上的虛擬裝置抽象概念。

### <a name="syntax"></a>語法

```
class accelerator_view;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[accelerator_view 建構函式](#ctor)|初始化 `accelerator_view` 類別的新執行個體。|
|[~ accelerator_view 解構函式](#dtor)|終結`accelerator_view`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[create_marker](#create_marker)|傳回追蹤的所有目前提交至此的命令完成的未來`accelerator_view`物件。|
|[flush](#flush)|提交所有暫止命令排入佇列`accelerator_view`至加速器以執行的物件。|
|[get_accelerator](#get_accelerator)|傳回 `accelerator` 物件的 `accelerator_view` 物件。|
|[get_is_auto_selection](#get_is_auto_selection)|傳回布林值，指出執行階段是否會自動選取適當的加速器時`accelerator_view`物件會傳遞給[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|
|[get_is_debug](#get_is_debug)|傳回布林值，指出是否`accelerator_view`物件具有擴充錯誤報告啟用偵錯層級。|
|[get_queuing_mode](#get_queuing_mode)|傳回的佇列模式`accelerator_view`物件。|
|[get_version](#get_version)|傳回的版本`accelerator_view`。|
|[等候](#wait)|等候所有的命令送出至`accelerator_view`完成的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|比較這個`accelerator_view`與另一個物件，然後傳回**false**它們是相同的; 否則會傳回**true**。|
|[operator=](#operator_eq)|將指定的內容複製`accelerator_view`到這個物件。|
|[operator==](#operator_eq_eq)|比較這個`accelerator_view`與另一個物件，然後傳回 **，則為 true**它們是相同的; 否則會傳回**false**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[accelerator](#accelerator)|取得 `accelerator_view` 物件的 `accelerator` 物件。|
|[is_auto_selection](#is_auto_selection)|取得布林值，指出執行階段是否會自動選取適當的加速器時`accelerator_view`物件會傳遞給[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|
|[is_debug](#is_debug)|取得布林值，指出是否`accelerator_view`物件具有擴充錯誤報告啟用偵錯層級。|
|[queuing_mode](#queuing_mode)|取得的佇列模式`accelerator_view`物件。|
|[version](#version)|取得加速器版本。|

## <a name="inheritance-hierarchy"></a>繼承階層

`accelerator_view`

### <a name="remarks"></a>備註

`accelerator_view`物件表示加速器的邏輯隔離檢視。 單一實體計算裝置可以有多個邏輯、 隔離`accelerator_view`物件。 每個加速器都有預設`accelerator_view`物件。 其他`accelerator_view`可以建立物件。

實體裝置，可在許多用戶端執行緒之間共用。 用戶端執行緒以合作方式可以使用相同`accelerator_view`物件的快速鍵或每個用戶端可以與透過獨立計算裝置通訊`accelerator_view`與其他用戶端執行緒隔離的物件。

`accelerator_view`物件可以是下列兩個[queuing_mode 列舉](concurrency-namespace-enums-amp.md#queuing_mode)狀態。 如果佇列模式`immediate`，命令喜歡`copy`和`parallel_for_each`只要傳回給呼叫者傳送至對應的加速器裝置。 如果佇列模式`deferred`，這類命令會排入對應至命令佇列`accelerator_view`物件。 命令實際上不會傳送到裝置，直到`flush()`呼叫。

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行

## <a name="accelerator"></a> 加速器

取得 accelerator_view 物件加速器物件。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a> accelerator_view

初始化 accelerator_view 類別的新執行個體，藉由複製現有`accelerator_view`物件。

### <a name="syntax"></a>語法

```
accelerator_view( const accelerator_view & _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`来複製的物件。

## <a name="accelerator_view__create_marker"></a> create_marker

傳回追蹤的所有目前提交至此的命令完成的未來`accelerator_view`物件。

### <a name="syntax"></a>語法

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>傳回值

若要追蹤的所有目前提交至此的命令完成的未來`accelerator_view`物件。

## <a name="flush"></a> 排清

送出至加速器以執行 accelerator_view 物件的所有暫止命令排入佇列。

### <a name="syntax"></a>語法

```
void flush();
```

### <a name="return-value"></a>傳回值

傳回 `void`。

## <a name="accelerator_view__get_accelerator"></a> get_accelerator

傳回 accelerator_view 物件的快速鍵對應物件。
### <a name="syntax"></a>語法

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>傳回值

Accelerator_view 物件加速器物件。

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection

傳回布林值，指出是否執行階段會自動選取適當的加速器時在 accelerator_view 傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。

### <a name="syntax"></a>語法

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>傳回值

**真**如果執行階段會自動選取適當的加速器;，否則為**false**。

## <a name="accelerator_view__get_is_debug"></a> get_is_debug

傳回布林值，指出 accelerator_view 物件是否有在擴充錯誤報告啟用偵錯層級。

### <a name="syntax"></a>語法

```
bool get_is_debug() const;
```

### <a name="return-value"></a>傳回值

布林值，指出是否`accelerator_view`物件具有擴充錯誤報告啟用偵錯層級。

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode

傳回 accelerator_view 物件的佇列模式。

### <a name="syntax"></a>語法

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>傳回值

佇列模式`accelerator_view`物件。

## <a name="accelerator_view__get_version"></a> get_version

傳回 accelerator_view 的版本。

### <a name="syntax"></a>語法

```
unsigned int get_version() const;
```

### <a name="return-value"></a>傳回值

新版`accelerator_view`。

## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection

取得布林值，指出是否執行階段會自動選取適當的加速器時在 accelerator_view 傳遞至[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="accelerator_view__is_debug"></a> is_debug

取得布林值，指出 accelerator_view 物件是否有在擴充錯誤報告啟用偵錯層級。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="accelerator_view__operator_neq"></a> 運算子 ！ =

比較這個 accelerator_view 物件與另一個，並傳回**假**相同; 否則會傳回 **，則為 true**。

### <a name="syntax"></a>語法

```
bool operator!= (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**false**兩個物件是否相同，否則 **，則為 true**。

## <a name="accelerator_view__operator_eq"></a> 運算子 =

將指定的 accelerator_view 物件的內容複製到這一個。

### <a name="syntax"></a>語法

```
accelerator_view & operator= (    const accelerator_view & _Other );
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`從複製的物件。

### <a name="return-value"></a>傳回值

已修改的參考`accelerator_view`物件。

## <a name="accelerator_view__operator_eq_eq"></a> 運算子 = =

比較這個 accelerator_view 物件與另一個，並傳回**真**相同; 否則會傳回**false**。

### <a name="syntax"></a>語法

```
bool operator= = (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>參數

*_Other*<br/>
`accelerator_view`要與這個比較的物件。

### <a name="return-value"></a>傳回值

**true**兩個物件是否相同，否則**false**。

## <a name="accelerator_view__queuing_mode"></a> queuing_mode

取得 accelerator_view 物件的佇列模式。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="accelerator_view__version"></a> 版本

取得 accelerator_view 的版本。

### <a name="syntax"></a>語法

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="accelerator_view__wait"></a> 等候

等候所有命令送出至 accelerator_view 物件來完成。

### <a name="syntax"></a>語法

```
void wait();
```

#### <a name="return-value"></a>傳回值

傳回 `void`。

#### <a name="remarks"></a>備註

如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)是`immediate`，這個方法會立即傳回而不會封鎖。

##  <a name="dtor"></a> ~ accelerator_view

終結 accelerator_view 物件。

#### <a name="syntax"></a>語法

```
~accelerator_view();
```

### <a name="return-value"></a>傳回值

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

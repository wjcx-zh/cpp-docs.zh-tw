---
title: CComSingleThreadModel 類別
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 05ef787764045ec7e17f5cdfdb0d4611cb2ac900
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229970"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 類別

這個類別會提供方法來遞增和遞減變數的值。

## <a name="syntax"></a>語法

```
class CComSingleThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CComSingleThreadModel：： CriticalSection](#criticalsection)|References 類別 `CComFakeCriticalSection` 。|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考 `CComSingleThreadModel` 。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComSingleThreadModel：:D ecrement](#decrement)|遞減指定變數的值。 此執行不是安全線程。|
|[CComSingleThreadModel：：遞增值](#increment)|遞增指定變數的值。 此執行不是安全線程。|

## <a name="remarks"></a>備註

`CComSingleThreadModel`提供方法來遞增和遞減變數的值。 不同于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這些方法並不是安全線程。

一般來說，您會使用 `CComSingleThreadModel` **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)這兩個名稱的其中一個。 每個所參考的類別都 **`typedef`** 取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程模型|單元執行緒模型|自由執行緒模型|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ;M =`CComMultiThreadModel`

`CComSingleThreadModel`本身會定義三個 **`typedef`** 名稱。 `ThreadModelNoCS`參考 `CComSingleThreadModel` 。 `AutoCriticalSection`和 `CriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，它會提供與取得和釋放重要區段擁有權相關聯的空白方法。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

使用時 `CComSingleThreadModel` ， **`typedef`** 名稱會 `AutoCriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

因為並未 `CComFakeCriticalSection` 提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定義 `AutoCriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `AutoCriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `AutoCriticalSection` ，您還可以使用 **`typedef`** 名稱[CriticalSection](#criticalsection)。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel：： CriticalSection

使用時 `CComSingleThreadModel` ， **`typedef`** 名稱會 `CriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

因為並未 `CComFakeCriticalSection` 提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定義 `CriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `CriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `CriticalSection` ，您還可以使用 **`typedef`** 名稱[AutoCriticalSection](#autocriticalsection)。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel：:D ecrement

此靜態函式會遞減*p*所指向之變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞減之變數的指標。

### <a name="return-value"></a>傳回值

遞減的結果。

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel：：遞增值

此靜態函式會遞增*p*所指向之變數的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞增之變數的指標。

### <a name="return-value"></a>傳回值

增量的結果。

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

使用時 `CComSingleThreadModel` ， **`typedef`** 名稱 `ThreadModelNoCS` 只會參考 `CComSingleThreadModel` 。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>備註

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含的定義 `ThreadModelNoCS` 。 下表顯示執行緒模型類別與所參考之類別之間的關聯性 `ThreadModelNoCS` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

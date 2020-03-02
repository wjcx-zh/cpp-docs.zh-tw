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
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215453"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel 類別

這個類別會提供方法來遞增和遞減變數的值。

## <a name="syntax"></a>語法

```
class CComSingleThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CComSingleThreadModel：： CriticalSection](#criticalsection)|參考類別 `CComFakeCriticalSection`。|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考 `CComSingleThreadModel`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComSingleThreadModel：:D ecrement](#decrement)|遞減指定變數的值。 此執行不是安全線程。|
|[CComSingleThreadModel：：遞增值](#increment)|遞增指定變數的值。 此執行不是安全線程。|

## <a name="remarks"></a>備註

`CComSingleThreadModel` 提供遞增和遞減變數值的方法。 不同于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這些方法並不是安全線程。

一般來說，您會透過[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)這兩個**typedef**名稱的其中一個來使用 `CComSingleThreadModel`。 每個**typedef**所參考的類別取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程模型|單元執行緒模型|自由執行緒模型|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

`CComSingleThreadModel` 本身會定義三個**typedef**名稱。 `ThreadModelNoCS` 參考 `CComSingleThreadModel`。 `AutoCriticalSection` 和 `CriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，它會提供與取得和釋放重要區段擁有權相關聯的空白方法。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

使用 `CComSingleThreadModel`時， **typedef**名稱 `AutoCriticalSection` 會參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

因為 `CComFakeCriticalSection` 不提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含 `AutoCriticalSection`的定義。 下表顯示執行緒模型類別和 `AutoCriticalSection`所參考的重要區段類別之間的關聯性：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了 `AutoCriticalSection`以外，您還可以使用**typedef**名稱[CriticalSection](#criticalsection)。 如果您想要排除 CRT 啟動程式碼，則不應該在全域物件或靜態類別成員中指定 `AutoCriticalSection`。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

##  <a name="criticalsection"></a>CComSingleThreadModel：： CriticalSection

使用 `CComSingleThreadModel`時， **typedef**名稱 `CriticalSection` 會參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

因為 `CComFakeCriticalSection` 不提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含 `CriticalSection`的定義。 下表顯示執行緒模型類別和 `CriticalSection`所參考的重要區段類別之間的關聯性：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了 `CriticalSection`以外，您還可以使用**typedef**名稱[AutoCriticalSection](#autocriticalsection)。 如果您想要排除 CRT 啟動程式碼，則不應該在全域物件或靜態類別成員中指定 `AutoCriticalSection`。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

##  <a name="decrement"></a>CComSingleThreadModel：:D ecrement

此靜態函式會遞減*p*所指向之變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
在要遞減之變數的指標。

### <a name="return-value"></a>傳回值

遞減的結果。

##  <a name="increment"></a>CComSingleThreadModel：：遞增值

此靜態函式會遞增*p*所指向之變數的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
在要遞增之變數的指標。

### <a name="return-value"></a>傳回值

增量的結果。

##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

使用 `CComSingleThreadModel`時， **typedef**名稱 `ThreadModelNoCS` 只是參考 `CComSingleThreadModel`。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>備註

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含 `ThreadModelNoCS`的定義。 下表顯示執行緒模型類別和 `ThreadModelNoCS`所參考的類別之間的關聯性：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)

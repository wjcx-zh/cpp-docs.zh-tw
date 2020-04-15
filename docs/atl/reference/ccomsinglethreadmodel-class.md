---
title: CCom 單線程式模型類別
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
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327325"
---
# <a name="ccomsinglethreadmodel-class"></a>CCom 單線程式模型類別

此類提供遞增和遞減變數值的方法。

## <a name="syntax"></a>語法

```
class CComSingleThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CCom 單線程模型::自動臨界部分](#autocriticalsection)|引用類別[CComFake 的界節](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CCom 單線程模型::關鍵部分](#criticalsection)|參考類別`CComFakeCriticalSection`。|
|[CCom 單線程模型::線程模型NoCS](#threadmodelnocs)|參考`CComSingleThreadModel`.|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 單線程模型::D](#decrement)|聲明指定變數的值。 此實現不是線程安全的。|
|[CCom 單線程模型:增量](#increment)|增加指定變數的值。 此實現不是線程安全的。|

## <a name="remarks"></a>備註

`CComSingleThreadModel`提供了遞增和遞減變數值的方法。 與[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModel NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)不同,這些方法不是線程安全的。

通常,您可以通過`CComSingleThreadModel`兩個**類型定義**名稱之一[(CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)或[CComGlobalsThreadModel)使用](atl-typedefs.md#ccomglobalsthreadmodel)。 每個**typedef**引用的類別取決於所使用的線程模型,如下表所示:

|typedef|單線程式模型|公寓線程模型|免費執行緒模型|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

`CComSingleThreadModel`本身定義三**個類型定義**名稱。 `ThreadModelNoCS`參考`CComSingleThreadModel`. `AutoCriticalSection`和`CriticalSection`引用類[CComFake 臨界節](../../atl/reference/ccomfakecriticalsection-class.md),它提供了與獲取和釋放關鍵部分的擁有權相關的空方法。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CCom 單線程模型::自動臨界部分

使用`CComSingleThreadModel`時 **,typedef**`AutoCriticalSection`名稱引用類別[CComFake 的臨界節](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

因為`CComFakeCriticalSection`不提供關鍵部分,因此其方法不執行任何操作。

[CCom 多線程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`AutoCriticalSection`的定義。 下表顯示了線程模型類與`AutoCriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除`AutoCriticalSection`之外 ,還可以使用**typedef**名稱[「臨界節](#criticalsection)」。。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CCom 單線程模型::關鍵部分

使用`CComSingleThreadModel`時 **,typedef**`CriticalSection`名稱引用類別[CComFake 的臨界節](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

因為`CComFakeCriticalSection`不提供關鍵部分,因此其方法不執行任何操作。

[CCom 多線程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`CriticalSection`的定義。 下表顯示了線程模型類與`CriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除`CriticalSection`之外 ,還可以使用**typedef**名稱[Auto 臨界節](#autocriticalsection)。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CCom 單線程模型::D

此靜態函數會遞減*p*指向的變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞減的變數的指標。

### <a name="return-value"></a>傳回值

遞減的結果。

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CCom 單線程模型:增量

此靜態函數遞增*p*指向的變數的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞增的變數的指標。

### <a name="return-value"></a>傳回值

增量的結果。

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 單線程模型::線程模型NoCS

使用`CComSingleThreadModel`時 **,typedef** `ThreadModelNoCS``CComSingleThreadModel`名稱只有參考 。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>備註

[CCom 多線程模型](../../atl/reference/ccommultithreadmodel-class.md)和[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)包含`ThreadModelNoCS`的定義。 下表顯示了線程模型類與 引用`ThreadModelNoCS`的 類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

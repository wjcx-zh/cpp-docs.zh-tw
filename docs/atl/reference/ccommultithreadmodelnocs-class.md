---
title: CComMultiThreadModelNoCS 類別
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: beb5cd1e13de1a10546f28d4a7eb98e45b6e9af1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224262"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS 類別

`CComMultiThreadModelNoCS`提供安全線程的方法，以遞增和遞減變數的值，而不需要重要區段鎖定或解除鎖定功能。

## <a name="syntax"></a>語法

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|Name|說明|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CComMultiThreadModelNoCS：： CriticalSection](#criticalsection)|References 類別 `CComFakeCriticalSection` 。|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|References 類別 `CComMultiThreadModelNoCS` 。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[CComMultiThreadModelNoCS：:D ecrement](#decrement)|靜止以執行緒安全的方式遞減指定變數的值。|
|[CComMultiThreadModelNoCS：：遞增值](#increment)|靜止以執行緒安全的方式遞增指定變數的值。|

## <a name="remarks"></a>備註

`CComMultiThreadModelNoCS`類似于[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) ，因為它提供安全線程方法來遞增和遞減變數。 不過，當您透過參考重要的區段類別時 `CComMultiThreadModelNoCS` ，和之類的方法 `Lock` `Unlock` 將不會執行任何動作。

一般來說，您會 `CComMultiThreadModelNoCS` 透過 `ThreadModelNoCS` **`typedef`** 名稱使用。 這 **`typedef`** 會在 `CComMultiThreadModelNoCS` 、 `CComMultiThreadModel` 和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)中定義。

> [!NOTE]
> 全域 **`typedef`** 名稱[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)不會參考 `CComMultiThreadModelNoCS` 。

除了之外，還會 `ThreadModelNoCS` `CComMultiThreadModelNoCS` 定義 `AutoCriticalSection` 和 `CriticalSection` 。 後面兩個 **`typedef`** 名稱會參考[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，這會提供與取得和釋放重要區段相關聯的空白方法。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

使用時 `CComMultiThreadModelNoCS` ， **`typedef`** 名稱會 `AutoCriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

因為並未 `CComFakeCriticalSection` 提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的定義 `AutoCriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `AutoCriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了之外 `AutoCriticalSection` ，您還可以使用 **`typedef`** 名稱[CriticalSection](#criticalsection)。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS：： CriticalSection

使用時 `CComMultiThreadModelNoCS` ， **`typedef`** 名稱會 `CriticalSection` 參考類別[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

因為並未 `CComFakeCriticalSection` 提供重要區段，所以其方法不會執行任何動作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的定義 `CriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `CriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了之外 `CriticalSection` ，您還可以使用 **`typedef`** 名稱 `AutoCriticalSection` 。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS：:D ecrement

這個靜態函式會呼叫 Win32 函式[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)，以遞減*p*所指向之變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞減之變數的指標。

### <a name="return-value"></a>傳回值

如果遞減的結果為0，則會傳回 `Decrement` 0。 如果遞減的結果不是零，則傳回值也不是零，但可能不等於遞減的結果。

### <a name="remarks"></a>備註

**InterlockedDecrement**可防止一個以上的執行緒同時使用此變數。

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS：：遞增值

這個靜態函式會呼叫 Win32 函式[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)，以遞增*p*所指向的變數值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞增之變數的指標。

### <a name="return-value"></a>傳回值

如果增量的結果為0，則**增量**會傳回0。 如果增量的結果不是零，則傳回值也是非零，但可能不等於增量的結果。

### <a name="remarks"></a>備註

**InterlockedIncrement**可防止一個以上的執行緒同時使用此變數。

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

使用時 `CComMultiThreadModelNoCS` ， **`typedef`** 名稱 `ThreadModelNoCS` 只會參考 `CComMultiThreadModelNoCS` 。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>備註

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)也包含的定義 `ThreadModelNoCS` 。 下表顯示執行緒模型類別與所參考之類別之間的關聯性 `ThreadModelNoCS` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

請注意，中的定義會 `ThreadModelNoCS` `CComMultiThreadModelNoCS` 提供與 `CComMultiThreadModel` 和的對稱 `CComSingleThreadModel` 。 例如，假設中的範例程式碼宣告 `CComMultiThreadModel::AutoCriticalSection` 如下 **`typedef`** ：

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

不論為指定的類別為何 `ThreadModel` （例如 `CComMultiThreadModelNoCS` ），都會 `_ThreadModel` 據以解決。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

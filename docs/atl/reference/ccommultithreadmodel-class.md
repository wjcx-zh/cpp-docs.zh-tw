---
title: CComMultiThreadModel 類別
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 38ed43e77492484b7c8d8cb06cad71e695d41c4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224275"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 類別

`CComMultiThreadModel`提供安全線程的方法，以遞增和遞減變數的值。

## <a name="syntax"></a>語法

```
class CComMultiThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CComMultiThreadModel：： CriticalSection](#criticalsection)|參考類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComMultiThreadModel：:D ecrement](#decrement)|靜止以執行緒安全的方式遞減指定變數的值。|
|[CComMultiThreadModel：：遞增值](#increment)|靜止以執行緒安全的方式遞增指定變數的值。|

## <a name="remarks"></a>備註

一般來說，您會使用 `CComMultiThreadModel` 透過兩個名稱的其中一個 **`typedef`** ，例如 [CComObjectThreadModel] （atl-typedef # CComObjectThreadModel 或 [CComGlobalsThreadModel] （atl-typedef # CComGlobalsThreadModel。 每個所參考的類別都 **`typedef`** 取決於所使用的執行緒模型，如下表所示：

|typedef|單一線程|單元執行緒|自由執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ;M =`CComMultiThreadModel`

`CComMultiThreadModel`本身會定義三個 **`typedef`** 名稱。 `AutoCriticalSection`和 `CriticalSection` 參考類別，提供取得和釋放重要區段之擁有權的方法。 `ThreadModelNoCS`references 類別 [CComMultiThreadModelNoCS （CComMultiThreadModelNoCS-class.md）。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

使用時 `CComMultiThreadModel` ， **`typedef`** 名稱會 `AutoCriticalSection` 參考類別[CComAutoCriticalSection](ccomautocriticalsection-class.md)，它會提供方法來取得和釋放重要區段物件的擁有權。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含的定義 `AutoCriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `AutoCriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `AutoCriticalSection` ，您還可以使用 **`typedef`** 名稱[CriticalSection](#criticalsection)。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

下列程式碼會在[CComObjectRootEx](ccomobjectrootex-class.md)之後模型化，並示範 `AutoCriticalSection` 線上程環境中使用。

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

下表顯示 `InternalAddRef` 和方法的結果，端 `Lock` 視 `ThreadModel` 應用程式所使用的範本參數和執行緒模型而定：

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|方法|單一或單元執行緒|自由執行緒|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是安全線程。|增量是安全線程。|
|`Lock`|不執行任何操作;沒有要鎖定的重要區段。|Critical 區段已鎖定。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel：： ThreadModelNoCS

|方法|單一或單元執行緒|自由執行緒|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是安全線程。|增量是安全線程。|
|`Lock`|不執行任何操作;沒有要鎖定的重要區段。|不執行任何操作;沒有要鎖定的重要區段。|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel：： CriticalSection

使用時 `CComMultiThreadModel` ， **`typedef`** 名稱會 `CriticalSection` 參考類別[CComCriticalSection](ccomcriticalsection-class.md)，它會提供方法來取得和釋放重要區段物件的擁有權。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含的定義 `CriticalSection` 。 下表顯示執行緒模型類別與所參考之 critical 區段類別之間的關聯性 `CriticalSection` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了之外 `CriticalSection` ，您還可以使用 **`typedef`** 名稱[AutoCriticalSection](#autocriticalsection)。 `AutoCriticalSection`如果您想要排除 CRT 啟始程式碼，則不應該在全域物件或靜態類別成員中指定。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](#autocriticalsection)。

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel：:D ecrement

這個靜態函式會呼叫 Win32 函式[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)，以遞減*p*所指向之變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞減之變數的指標。

### <a name="return-value"></a>傳回值

如果遞減的結果為0，則會傳回 `Decrement` 0。 如果遞減的結果不是零，則傳回值也不是零，但可能不等於遞減的結果。

### <a name="remarks"></a>備註

`InterlockedDecrement`防止一個以上的執行緒同時使用這個變數。

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel：：遞增值

這個靜態函式會呼叫 Win32 函式[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)，以遞增*p*所指向的變數值。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*p&id*<br/>
在要遞增之變數的指標。

### <a name="return-value"></a>傳回值

如果增量的結果為0，則會傳回 `Increment` 0。 如果增量的結果不是零，則傳回值也是非零，但可能不等於增量的結果。

### <a name="remarks"></a>備註

`InterlockedIncrement`防止一個以上的執行緒同時使用這個變數。

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

使用時 `CComMultiThreadModel` ， **`typedef`** 名稱會 `ThreadModelNoCS` 參考類別[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>備註

`CComMultiThreadModelNoCS`提供安全線程方法來遞增和遞減變數;不過，它不會提供重要區段。

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)和 `CComMultiThreadModelNoCS` 也包含的定義 `ThreadModelNoCS` 。 下表顯示執行緒模型類別與所參考之類別之間的關聯性 `ThreadModelNoCS` ：

|類別定義于|參考的類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CComMultiThreadModel：： AutoCriticalSection](#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[CComSingleThreadModel 類別](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection 類別](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection 類別](ccomcriticalsection-class.md)<br/>
[類別概觀](../atl-class-overview.md)

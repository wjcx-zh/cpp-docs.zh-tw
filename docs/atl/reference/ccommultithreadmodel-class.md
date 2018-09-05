---
title: CComMultiThreadModel 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33eac78dc871dd2a9869452bc829150c3356fd0a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754939"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel 類別

`CComMultiThreadModel` 提供安全執行緒方法遞增和遞減變數的值。

## <a name="syntax"></a>語法

```
class CComMultiThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|參考類別[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|參考類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|參考類別[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|（靜態）遞減以執行緒安全的方式指定變數的值。|
|[CComMultiThreadModel::Increment](#increment)|（靜態）以執行緒安全的方式遞增指定變數的值。|

## <a name="remarks"></a>備註

一般而言，您可以使用`CComMultiThreadModel`透過其中兩個**typedef**名稱，其中一個 [CComObjectThreadModel] (atl typedefs.md #ccomobjectthreadmodel 或 [CComGlobalsThreadModel] (atl typedefs.md #ccomglobalsthreadmodel。 每個參考的類別**typedef**取決於執行緒模型，如下表所示：

|typedef|單一執行緒處理|Apartment 執行緒|無限制執行緒|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

`CComMultiThreadModel` 本身會定義三個**typedef**名稱。 `AutoCriticalSection` 和`CriticalSection`參考類別，可提供方法取得和釋放重要區段的擁有權。 `ThreadModelNoCS` 參考類別 [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md)。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

使用時`CComMultiThreadModel`，則**typedef**名稱`AutoCriticalSection`參考類別[CComAutoCriticalSection](ccomautocriticalsection-class.md)，這會提供方法，來取得和釋放重要區段的擁有權物件。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)並[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含定義`AutoCriticalSection`。 下表顯示執行緒的模型類別所參考的關鍵區段類別之間的關聯性`AutoCriticalSection`:

|在定義類別|參考類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了`AutoCriticalSection`，您可以使用**typedef**名稱[CriticalSection](#criticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要消除 CRT 啟始程式碼中。

### <a name="example"></a>範例

下列程式碼仿造[CComObjectRootEx](ccomobjectrootex-class.md)，並示範`AutoCriticalSection`執行緒環境中使用。

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

下表顯示的結果`InternalAddRef`並`Lock`方法，取決於`ThreadModel`樣板參數和應用程式所使用的執行緒模型：

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|方法|單一或 Apartment 執行緒|無限制執行緒|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不具備執行緒安全。|的增量是安全執行緒。|
|`Lock`|沒有任何作用;沒有任何鎖定的重要區段。|已鎖定重要區段。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|方法|單一或 Apartment 執行緒|無限制執行緒|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不具備執行緒安全。|的增量是安全執行緒。|
|`Lock`|沒有任何作用;沒有任何鎖定的重要區段。|沒有任何作用;沒有任何鎖定的重要區段。|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

使用時`CComMultiThreadModel`，則**typedef**名稱`CriticalSection`參考類別[CComCriticalSection](ccomcriticalsection-class.md)，這會提供方法，來取得和釋放重要區段物件的擁有權。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)並[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)也包含定義`CriticalSection`。 下表顯示執行緒的模型類別所參考的關鍵區段類別之間的關聯性`CriticalSection`:

|在定義類別|參考類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除了`CriticalSection`，您可以使用**typedef**名稱[AutoCriticalSection](#autocriticalsection)。 您不應該指定`AutoCriticalSection`全域物件或靜態類別成員，如果您想要消除 CRT 啟始程式碼中。

### <a name="example"></a>範例

請參閱[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

此靜態函式會呼叫 Win32 函式[InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement)，變數的值所指向的遞減*p*。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*p*  
[in]要遞減之變數的指標。

### <a name="return-value"></a>傳回值

如果遞減的結果是 0，則`Decrement`會傳回 0。 如果是非零值的遞減結果，傳回值也為非零值，但可能不等於遞減的結果。

### <a name="remarks"></a>備註

`InterlockedDecrement` 防止多個執行緒同時使用此變數。

##  <a name="increment"></a>  CComMultiThreadModel::Increment

此靜態函式會呼叫 Win32 函式[InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement)，這會遞增變數所指向的值*p*。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*p*  
[in]要遞增之變數的指標。

### <a name="return-value"></a>傳回值

如果增量的結果是 0，則`Increment`會傳回 0。 如果增量的結果為非零值，傳回的值也是零，但可能不會等於增量的結果。

### <a name="remarks"></a>備註

`InterlockedIncrement` 防止多個執行緒同時使用此變數。

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

使用時`CComMultiThreadModel`，則**typedef**名稱`ThreadModelNoCS`參考類別[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>備註

`CComMultiThreadModelNoCS` 遞增和遞減變數，提供安全執行緒方法不過，它不會提供重要的區段。

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)並`CComMultiThreadModelNoCS`也包含定義`ThreadModelNoCS`。 下表顯示執行緒的模型類別與所參考的類別之間的關聯性`ThreadModelNoCS`:

|在定義類別|參考類別|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[CComSingleThreadModel 類別](ccomsinglethreadmodel-class.md)   
[CComAutoCriticalSection 類別](ccomautocriticalsection-class.md)   
[CComCriticalSection 類別](ccomcriticalsection-class.md)   
[類別概觀](../atl-class-overview.md)

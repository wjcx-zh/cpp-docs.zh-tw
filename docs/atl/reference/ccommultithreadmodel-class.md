---
title: CCom 多線程式模型類別
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
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327662"
---
# <a name="ccommultithreadmodel-class"></a>CCom 多線程式模型類別

`CComMultiThreadModel`提供線程安全方法,用於遞增和遞減變數的值。

## <a name="syntax"></a>語法

```
class CComMultiThreadModel
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CCom 多線程模型::自動臨界部分](#autocriticalsection)|參考類別[CComAuto 的臨界節](../../atl/reference/ccomautocriticalsection-class.md)。|
|[CCom 多線程模型::關鍵部分](#criticalsection)|參考類別[CCom 臨界節](../../atl/reference/ccomcriticalsection-class.md)。|
|[CCom 多線程模型::線程模型NoCS](#threadmodelnocs)|引用類別[CCom 多線程式Name NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 多線程模型::D](#decrement)|(靜態)以線程安全的方式聲明指定變數的值。|
|[CCom 多線程模型:增量](#increment)|(靜態)以線程安全的方式遞增指定變數的值。|

## <a name="remarks"></a>備註

通常,您可以通過`CComMultiThreadModel`兩 個**類型定義**名稱之一使用,即 [CcomObjectThreadModel](atl typedefs.md_ccomobjectthreadmodel 或 [CcomGlobalsThreadModel](atl-typedefs.md_ccomglobalsthreadmodel)。 每個**typedef**引用的類別取決於所使用的線程模型,如下表所示:

|typedef|單線程|公寓線程|免費線程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

`CComMultiThreadModel`本身定義三**個類型定義**名稱。 `AutoCriticalSection`和`CriticalSection`提供獲取和釋放關鍵部分擁有權的方法的引用類。 `ThreadModelNoCS`引用類 _CComMultiThreadModelNoCS(ccom 多線程模型-class.md)。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CCom 多線程模型::自動臨界部分

使用`CComMultiThreadModel`時 **,typedef**`AutoCriticalSection`名稱引用類[CComAuto 臨界節](ccomautocriticalsection-class.md),它提供了獲取和釋放關鍵節物件擁有權的方法。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

[CCom 單線程模型](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)還包含`AutoCriticalSection`的定義。 下表顯示了線程模型類與`AutoCriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除`AutoCriticalSection`之外 ,還可以使用**typedef**名稱[「臨界節](#criticalsection)」。。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

以下代碼以[CcomObjectRootEx](ccomobjectrootex-class.md)建模,`AutoCriticalSection`並展示 線上程環境中使用。

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

下表顯示了`InternalAddRef``Lock`和 方法的結果,`ThreadModel`具體取決於 樣本參數和應用程式使用的線程模型:

### <a name="threadmodel--ccomobjectthreadmodel"></a>執行緒模型 = CComobject 執行緒模型

|方法|單線程式與公寓線程|免費線程|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是線程安全的。|增量是線程安全的。|
|`Lock`|什麼都不做;沒有要鎖定的關鍵部分。|關鍵部分已鎖定。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>執行緒模型 = CComobject 執行緒模型::執行緒模型NoCS

|方法|單線程式與公寓線程|免費線程|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|增量不是線程安全的。|增量是線程安全的。|
|`Lock`|什麼都不做;沒有要鎖定的關鍵部分。|什麼都不做;沒有要鎖定的關鍵部分。|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CCom 多線程模型::關鍵部分

使用`CComMultiThreadModel`時 **,typedef**`CriticalSection`名稱引用類[CCom 臨界節](ccomcriticalsection-class.md),它提供了獲取和釋放關鍵節物件擁有權的方法。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

[CCom 單線程模型](ccomsinglethreadmodel-class.md)和[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)還包含`CriticalSection`的定義。 下表顯示了線程模型類與`CriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

除`CriticalSection`之外 ,還可以使用**typedef**名稱[Auto 臨界節](#autocriticalsection)。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](#autocriticalsection)。

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CCom 多線程模型::D

此靜態函數調用 Win32 函數[互鎖聲明](/windows/win32/api/winnt/nf-winnt-interlockeddecrement),它遞減*p*指向的變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞減的變數的指標。

### <a name="return-value"></a>傳回值

如果遞減的結果為 0,`Decrement`則返回 0。 如果遞減的結果為非零,則返回值也是非零,但可能不等於遞減的結果。

### <a name="remarks"></a>備註

`InterlockedDecrement`防止多個線程同時使用此變數。

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CCom 多線程模型:增量

此靜態函數調用 Win32 函數[互鎖增量](/windows/win32/api/winnt/nf-winnt-interlockedincrement),它遞增*p*指向的變數的值。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞增的變數的指標。

### <a name="return-value"></a>傳回值

如果增量的結果為 0,`Increment`則返回 0。 如果增量的結果是非零,則返回值也是非零,但可能不等於增量的結果。

### <a name="remarks"></a>備註

`InterlockedIncrement`防止多個線程同時使用此變數。

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 多線程模型::線程模型NoCS

使用`CComMultiThreadModel`時 **,typedef**`ThreadModelNoCS`名稱引用類別[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>備註

`CComMultiThreadModelNoCS`提供線程安全方法,用於遞增和遞減變數;但是,它不提供關鍵部分。

[CComSingleThreadModel,](ccomsinglethreadmodel-class.md)`CComMultiThreadModelNoCS`並包含的`ThreadModelNoCS`定義 。 下表顯示了線程模型類與 引用`ThreadModelNoCS`的 類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[CCom 單線程式模型類別](ccomsinglethreadmodel-class.md)<br/>
[CComAuto關鍵科類別](ccomautocriticalsection-class.md)<br/>
[CCom臨界節類](ccomcriticalsection-class.md)<br/>
[類別概觀](../atl-class-overview.md)

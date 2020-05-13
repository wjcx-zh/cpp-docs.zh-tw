---
title: CCom 多線程式程式
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
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327657"
---
# <a name="ccommultithreadmodelnocs-class"></a>CCom 多線程式程式

`CComMultiThreadModelNoCS`提供線程安全方法,用於遞增和遞減變數的值,而無需關鍵截面鎖定或解鎖功能。

## <a name="syntax"></a>語法

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CCom 多線程模型NoCS::自動臨界部分](#autocriticalsection)|引用類別[CComFake 的界節](../../atl/reference/ccomfakecriticalsection-class.md)。|
|[CCom 多線程模型NoCS::關鍵部分](#criticalsection)|參考類別`CComFakeCriticalSection`。|
|[CCom 多線程模型NoCS::執行緒模型NoCS](#threadmodelnocs)|參考類別`CComMultiThreadModelNoCS`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 多線程模型NoCS::D](#decrement)|(靜態)以線程安全的方式聲明指定變數的值。|
|[CCom 多線程模型NoCS::增量](#increment)|(靜態)以線程安全的方式遞增指定變數的值。|

## <a name="remarks"></a>備註

`CComMultiThreadModelNoCS`與[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)類似,因為它提供了用於遞增和遞減變數的線程安全方法。 但是,當您通過`CComMultiThreadModelNoCS`引用關鍵節類時,方法如`Lock``Unlock`和將不執行任何操作。

通常,您可以`CComMultiThreadModelNoCS``ThreadModelNoCS`通過**typedef**名稱使用。 這個**型態def**在`CComMultiThreadModelNoCS`中`CComMultiThreadModel`定義, 與[CCom 單線程式 。](../../atl/reference/ccomsinglethreadmodel-class.md)

> [!NOTE]
> 全域**型態定義**[名稱 CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)和[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)`CComMultiThreadModelNoCS`不引用 。

除了`ThreadModelNoCS`之外,`CComMultiThreadModelNoCS``AutoCriticalSection`定義`CriticalSection`與 。 后兩**個類型定義**名稱引用[CComFake 臨界節](../../atl/reference/ccomfakecriticalsection-class.md),它提供了與獲取和釋放關鍵部分相關的空方法。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CCom 多線程模型NoCS::自動臨界部分

使用`CComMultiThreadModelNoCS`時 **,typedef**`AutoCriticalSection`名稱引用類別[CComFake 的臨界節](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>備註

因為`CComFakeCriticalSection`不提供關鍵部分,因此其方法不執行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 單線程模型](../../atl/reference/ccomsinglethreadmodel-class.md)還包含`AutoCriticalSection`的定義。 下表顯示了線程模型類與`AutoCriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除`AutoCriticalSection`之外 ,還可以使用**typedef**名稱[「臨界節](#criticalsection)」。。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CCom 多線程模型NoCS::關鍵部分

使用`CComMultiThreadModelNoCS`時 **,typedef**`CriticalSection`名稱引用類別[CComFake 的臨界節](../../atl/reference/ccomfakecriticalsection-class.md)。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>備註

因為`CComFakeCriticalSection`不提供關鍵部分,因此其方法不執行任何操作。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 單線程模型](../../atl/reference/ccomsinglethreadmodel-class.md)還包含`CriticalSection`的定義。 下表顯示了線程模型類與`CriticalSection`引用 的關鍵節類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

除了之外`CriticalSection`,還可以使用**typedef**名稱`AutoCriticalSection`。 如果要消除 CRT 啟動代碼,不應在全域物件或靜態類別成員中`AutoCriticalSection`指定 。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CCom 多線程模型NoCS::D

此靜態函數調用 Win32 函數[互鎖聲明](/windows/win32/api/winnt/nf-winnt-interlockeddecrement),它遞減*p*指向的變數的值。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞減的變數的指標。

### <a name="return-value"></a>傳回值

如果遞減的結果為 0,`Decrement`則返回 0。 如果遞減的結果為非零,則返回值也是非零,但可能不等於遞減的結果。

### <a name="remarks"></a>備註

**互鎖的"聲明"** 可防止多個線程同時使用此變數。

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CCom 多線程模型NoCS::增量

此靜態函數調用 Win32 函數[互鎖增量](/windows/win32/api/winnt/nf-winnt-interlockedincrement),它遞增*p*指向的變數的值。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向要遞增的變數的指標。

### <a name="return-value"></a>傳回值

如果增量的結果為 0,則**增量**返回 0。 如果增量的結果是非零,則返回值也是非零,但可能不等於增量的結果。

### <a name="remarks"></a>備註

**互鎖增量**可防止多個線程同時使用此變數。

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CCom 多線程模型NoCS::執行緒模型NoCS

使用`CComMultiThreadModelNoCS`時 **,typedef** `ThreadModelNoCS``CComMultiThreadModelNoCS`名稱只有參考 。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>備註

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)和[CCom 單線程模型](../../atl/reference/ccomsinglethreadmodel-class.md)還包含`ThreadModelNoCS`的定義。 下表顯示了線程模型類與 引用`ThreadModelNoCS`的 類之間的關係:

|類別定義在|引用的類|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

請注意`ThreadModelNoCS`,`CComMultiThreadModelNoCS`中的定義提供了`CComMultiThreadModel``CComSingleThreadModel`與 和 的對稱性。 例如,假設聲明的以下`CComMultiThreadModel::AutoCriticalSection`**typedef**中的範例碼 :

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

無論為`ThreadModel`(`CComMultiThreadModelNoCS`如 )`_ThreadModel`指定的類 如何,都會相應地解析。

### <a name="example"></a>範例

請參閱[CCom 多線程模型::自動臨界節](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

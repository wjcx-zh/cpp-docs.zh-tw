---
title: CAutoPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 699e62362bc74009e3faed3b4fd66b579c9c4cd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226655"
---
# <a name="cautoptr-class"></a>CAutoPtr 類別

此類別代表智慧型指標物件。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>參數

*T*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|建構函式。|
|[CAutoPtr：： ~ CAutoPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAutoPtr：： Attach](#attach)|呼叫此方法以取得現有指標的擁有權。|
|[CAutoPtr：:D etach](#detach)|呼叫此方法以釋放指標的擁有權。|
|[CAutoPtr：： Free](#free)|呼叫這個方法，以刪除所指向的物件 `CAutoPtr` 。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CAutoPtr：： operator T *](#operator_t_star)|Cast 運算子。|
|[CAutoPtr：： operator =](#operator_eq)|指派運算子。|
|[CAutoPtr：： operator->](#operator_ptr)|成員指標運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CAutoPtr：： m_p](#m_p)|指標資料成員變數。|

## <a name="remarks"></a>備註

此類別提供建立和管理智慧型指標的方法，其可在超出範圍時自動釋放資源，協助防止記憶體流失。

此外，的複製的「程式」 `CAutoPtr` 和「指派」運算子會轉移指標的擁有權，將來源指標複製到目的地指標，並將來源指標設定為 Null。 因此，不可能有兩 `CAutoPtr` 個物件儲存相同的指標，這可減少刪除相同指標兩次的可能性。

`CAutoPtr`也簡化了指標集合的建立。 除了衍生集合類別和覆寫析構函式，更容易建立 `CAutoPtr` 物件集合。 刪除集合時， `CAutoPtr` 物件將會超出範圍，並自動予以刪除。

[CHeapPtr](../../atl/reference/cheapptr-class.md)和 variant 的運作方式與相同 `CAutoPtr` ，不同之處在于它們會使用不同的堆積函數來配置和釋放記憶體，而不是 c + + **`new`** 和 **`delete`** 運算子。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)類似 `CAutoPtr` ，唯一的差別在於它使用**vector new []** 和**vector delete []** 來配置和釋放記憶體。

當需要陣列或智慧型指標清單時，另請參閱[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md) 。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr：： Attach

呼叫此方法以取得現有指標的擁有權。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
`CAutoPtr`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

當 `CAutoPtr` 物件取得指標的擁有權時，它會在超出範圍時，自動刪除指標和任何已配置的資料。 如果呼叫[CAutoPtr：:D etach](#detach) ，則程式設計人員會再次負責釋放任何已配置的資源。

在 [偵錯工具] 組建中，如果[CAutoPtr：： m_p](#m_p)資料成員目前指向現有的值，就會發生判斷提示失敗;也就是，它不等於 Null。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

建構函式。

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
現有的指標。

*TSrc*<br/>
由另一個管理的類型 `CAutoPtr` ，用來初始化目前的物件。

### <a name="remarks"></a>備註

`CAutoPtr`物件可以使用現有的指標來建立，在此情況下，它會傳輸指標的擁有權。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr：： ~ CAutoPtr

解構函式。

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>備註

釋放任何已配置的資源。 呼叫[CAutoPtr：： Free](#free)。

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr：:D etach

呼叫此方法以釋放指標的擁有權。

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回指標的複本。

### <a name="remarks"></a>備註

釋放指標的擁有權，將[CAutoPtr：： m_p](#m_p)資料成員變數設定為 Null，並傳回指標的複本。 呼叫之後 `Detach` ，程式設計人員會自行釋放任何已配置的資源，供 `CAutoPtr` 物件先前假設為 reponsibility。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr：： Free

呼叫這個方法，以刪除所指向的物件 `CAutoPtr` 。

```cpp
void Free() throw();
```

### <a name="remarks"></a>備註

會釋放所指向的物件 `CAutoPtr` ，而且[CAutoPtr：： m_p](#m_p)資料成員變數會設定為 Null。

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr：： m_p

指標資料成員變數。

```cpp
T* m_p;
```

### <a name="remarks"></a>備註

這個成員變數會保存指標資訊。

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr：： operator =

指派運算子。

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>參數

*p&id*<br/>
指標。

*TSrc*<br/>
類別類型。

### <a name="return-value"></a>傳回值

傳回對**CAutoPtr \< T > **的參考。

### <a name="remarks"></a>備註

指派運算子會 `CAutoPtr` 從任何目前的指標卸離物件，並將新的指標（ *p*）附加至其位置。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr：： operator-&gt;

成員指標運算子。

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>傳回值

傳回[CAutoPtr：： m_p](#m_p)資料成員變數的值。

### <a name="remarks"></a>備註

使用這個運算子，即可呼叫物件所指向之類別中的方法 `CAutoPtr` 。 在 [偵錯工具] 組建中，如果指向 Null，就會發生判斷提示失敗 `CAutoPtr` 。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr：： operator T *

Cast 運算子。

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>傳回值

傳回類別樣板中所定義之物件資料類型的指標。

### <a name="example"></a>範例

請參閱[CAutoPtr 總覽](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

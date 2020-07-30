---
title: CAutoVectorPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 65d37396b02d2c11c758915b201eef09cf1935b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226642"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 類別

此類別代表使用向量 new 和 delete 運算子的智慧型指標物件。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>參數

*T*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|建構函式。|
|[CAutoVectorPtr：： ~ CAutoVectorPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAutoVectorPtr：： Allocate](#allocate)|呼叫這個方法，以配置所指向之物件陣列所需的記憶體 `CAutoVectorPtr` 。|
|[CAutoVectorPtr：： Attach](#attach)|呼叫此方法以取得現有指標的擁有權。|
|[CAutoVectorPtr：:D etach](#detach)|呼叫此方法以釋放指標的擁有權。|
|[CAutoVectorPtr：： Free](#free)|呼叫這個方法，以刪除所指向的物件 `CAutoVectorPtr` 。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CAutoVectorPtr：： operator T *](#operator_t__star)|Cast 運算子。|
|[CAutoVectorPtr：： operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CAutoVectorPtr：： m_p](#m_p)|指標資料成員變數。|

## <a name="remarks"></a>備註

此類別提供建立和管理智慧型指標的方法，其可在超出範圍時自動釋放資源，協助防止記憶體流失。 `CAutoVectorPtr`類似于 `CAutoPtr` ，唯一的差異在於 `CAutoVectorPtr` 使用[向量 new&#91;&#93;](../../standard-library/new-operators.md#op_new_arr)和[vector delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr)來配置和釋放記憶體，而不是 c + + **`new`** 和 **`delete`** 運算子。 如需的集合類別，請參閱[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) `CAutoVectorPtr` 。

如需使用智慧型指標類別的範例，請參閱[CAutoPtr](../../atl/reference/cautoptr-class.md) 。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr：： Allocate

呼叫這個方法，以配置所指向之物件陣列所需的記憶體 `CAutoVectorPtr` 。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>參數

*nElements*<br/>
陣列中的項目數。

### <a name="return-value"></a>傳回值

如果成功配置記憶體，則傳回 true，否則會傳回 false。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果[CAutoVectorPtr：： m_p](#m_p)成員變數目前指向現有的值，就會發生判斷提示失敗;也就是，它不等於 Null。

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr：： Attach

呼叫此方法以取得現有指標的擁有權。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
`CAutoVectorPtr`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

當 `CAutoVectorPtr` 物件取得指標的擁有權時，它會在超出範圍時，自動刪除指標和任何已配置的資料。 如果呼叫[CAutoVectorPtr：:D etach](#detach) ，則程式設計人員會再次負責釋放任何已配置的資源。

在 [偵錯工具] 組建中，如果[CAutoVectorPtr：： m_p](#m_p)成員變數目前指向現有的值，就會發生判斷提示失敗;也就是，它不等於 Null。

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

建構函式。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
現有的指標。

### <a name="remarks"></a>備註

`CAutoVectorPtr`物件可以使用現有的指標來建立，在此情況下，它會傳輸指標的擁有權。

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr：： ~ CAutoVectorPtr

解構函式。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>備註

釋放任何已配置的資源。 呼叫[CAutoVectorPtr：： Free](#free)。

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr：:D etach

呼叫此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回指標的複本。

### <a name="remarks"></a>備註

釋放指標的擁有權，將[CAutoVectorPtr：： m_p](#m_p)成員變數設定為 Null，並傳回指標的複本。 呼叫之後 `Detach` ，程式設計人員會自行釋放任何已配置的資源，供該 `CAutoVectorPtr` 物件先前被視為責任。

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr：： Free

呼叫這個方法，以刪除所指向的物件 `CAutoVectorPtr` 。

```cpp
void Free() throw();
```

### <a name="remarks"></a>備註

會釋放所指向的物件 `CAutoVectorPtr` ，而且[CAutoVectorPtr：： m_p](#m_p)成員變數會設定為 Null。

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr：： m_p

指標資料成員變數。

```
T* m_p;
```

### <a name="remarks"></a>備註

這個成員變數會保存指標資訊。

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr：： operator =

指派運算子。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p&id*<br/>
指標。

### <a name="return-value"></a>傳回值

傳回對**CAutoVectorPtr \< T > **的參考。

### <a name="remarks"></a>備註

指派運算子會 `CAutoVectorPtr` 從任何目前的指標卸離物件，並將新的指標（ *p*）附加至其位置。

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr：： operator T *

Cast 運算子。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

傳回類別樣板中所定義之物件資料類型的指標。

## <a name="see-also"></a>另請參閱

[CAutoPtr 類別](../../atl/reference/cautoptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

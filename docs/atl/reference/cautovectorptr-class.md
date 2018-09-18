---
title: CAutoVectorPtr 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d60a7f40fc90d5586d7a8a7d41cab81a4d97c85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054476"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr 類別

此類別代表使用新的向量的智慧型指標物件和 delete 運算子。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|建構函式。|
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtr::Allocate](#allocate)|呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。|
|[CAutoVectorPtr::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|
|[CAutoVectorPtr::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|
|[CAutoVectorPtr::Free](#free)|呼叫這個方法來刪除所指向的物件`CAutoVectorPtr`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|轉換運算子。|
|[CAutoVectorPtr::operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|指標的資料成員變數中。|

## <a name="remarks"></a>備註

這個類別提供方法來建立和管理智慧型指標，這有助於防止記憶體流失，自動在它超出範圍時釋出資源。 `CAutoVectorPtr` 類似於`CAutoPtr`、 唯一的差別在於，`CAutoVectorPtr`會使用[向量的新&#91;&#93; ](../../standard-library/new-operators.md#op_new_arr)並[向量刪除&#91;&#93; ](../../standard-library/new-operators.md#op_delete_arr)來配置和釋放記憶體而不是 c + +**新**並**刪除**運算子。 請參閱[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)如果集合類別的`CAutoVectorPtr`所需。

請參閱[CAutoPtr](../../atl/reference/cautoptr-class.md)使用智慧型指標類別的範例。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="allocate"></a>  CAutoVectorPtr::Allocate

呼叫這個方法來配置所指向的物件陣列所需的記憶體`CAutoVectorPtr`。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>參數

*nElements*<br/>
陣列中的項目數。

### <a name="return-value"></a>傳回值

如果記憶體已成功則傳回 true 配置失敗的 false。

### <a name="remarks"></a>備註

在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數現在會指向現有的值; 也就是說，不等於 NULL。

##  <a name="attach"></a>  CAutoVectorPtr::Attach

呼叫這個方法來取得現有指標的擁有權。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
`CAutoVectorPtr`物件會取得這個指標的擁有權。

### <a name="remarks"></a>備註

當`CAutoVectorPtr`物件會採用指標的擁有權，則會自動刪除的指標和配置的任何資料時超出範圍。 如果[CAutoVectorPtr::Detach](#detach)是呼叫，程式設計人員再次指定負責釋放任何配置的資源。

在偵錯組建中，如果，就會發生判斷提示失敗[CAutoVectorPtr::m_p](#m_p)成員變數現在會指向現有的值; 也就是說，不等於 NULL。

##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr

建構函式。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
現有的指標。

### <a name="remarks"></a>備註

`CAutoVectorPtr`可以使用現有的指標建立物件，在此情況下傳送的是指標的擁有權。

##  <a name="dtor"></a>  CAutoVectorPtr:: ~ CAutoVectorPtr

解構函式。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>備註

會釋放所有配置的資源。 呼叫[CAutoVectorPtr::Free](#free)。

##  <a name="detach"></a>  CAutoVectorPtr::Detach

呼叫此方法，以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回指標的複本。

### <a name="remarks"></a>備註

釋放指標的擁有權、 設定[CAutoVectorPtr::m_p](#m_p)成員變數為 NULL，並傳回指標的複本。 之後呼叫`Detach`，它最多程式設計師可以釋放任何配置的資源，哪些`CAutoVectorPtr`物件可能先前假設責任。

##  <a name="free"></a>  CAutoVectorPtr::Free

呼叫這個方法來刪除所指向的物件`CAutoVectorPtr`。

```
void Free() throw();
```

### <a name="remarks"></a>備註

指向的物件`CAutoVectorPtr`釋出，而[CAutoVectorPtr::m_p](#m_p)成員變數會設為 NULL。

##  <a name="m_p"></a>  CAutoVectorPtr::m_p

指標的資料成員變數中。

```
T* m_p;
```

### <a name="remarks"></a>備註

此成員變數會保留指標資訊。

##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =

指派運算子。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
變數的指標。

### <a name="return-value"></a>傳回值

傳回的參考**CAutoVectorPtr\< T >**。

### <a name="remarks"></a>備註

指派運算子會卸離`CAutoVectorPtr`物件從目前的指標並附加新的指標*p*，在其位置。

##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *

轉換運算子。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

傳回類別範本中定義的物件資料類型的指標。

## <a name="see-also"></a>另請參閱

[CAutoPtr 類別](../../atl/reference/cautoptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

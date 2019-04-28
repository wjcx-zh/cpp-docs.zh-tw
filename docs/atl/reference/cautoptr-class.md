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
ms.openlocfilehash: 7f4f446aa97f2bf3843b830bd7fb4c4a5d74ffdb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260158"
---
# <a name="cautoptr-class"></a>CAutoPtr 類別

此類別代表智慧型指標物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>參數

*T*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|建構函式。|
|[CAutoPtr::~CAutoPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|
|[CAutoPtr::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|
|[CAutoPtr::Free](#free)|呼叫這個方法來刪除所指向的物件`CAutoPtr`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::operator T*](#operator_t_star)|轉換運算子。|
|[CAutoPtr::operator =](#operator_eq)|指派運算子。|
|[CAutoPtr::operator ->](#operator_ptr)|成員指標運算子中。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|指標的資料成員變數中。|

## <a name="remarks"></a>備註

這個類別提供方法來建立和管理智慧型指標，這有助於防止記憶體流失，自動在它超出範圍時釋出資源。

此外，`CAutoPtr`的複製建構函式和指派運算子轉移擁有權的指標，請將與來源指標複製到目的地的指標，並設定與來源指標為 NULL。 因此不可能有兩個`CAutoPtr`物件每個儲存相同的指標，以及這會減少兩次刪除相同的指標的可能性。

`CAutoPtr` 也可以簡化建立集合的指標。 而不是衍生的集合類別，並覆寫解構函式，是讓集合的工作變得更容易`CAutoPtr`物件。 刪除集合時，`CAutoPtr`物件會超出範圍而自動刪除其本身。

[CHeapPtr](../../atl/reference/cheapptr-class.md)變體運作方式與`CAutoPtr`，差異在於它們配置和釋放記憶體使用不同的堆積函式，而不是C++**新**並**刪除**運算子。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)大致`CAutoPtr`、 唯一的差別在於它會使用**vector new []** 並**向量 delete []** 來配置和釋放記憶體。

另請參閱[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)並[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)陣列或清單的智慧型指標需要時。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

##  <a name="attach"></a>  CAutoPtr::Attach

呼叫這個方法來取得現有指標的擁有權。

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
`CAutoPtr`物件會取得這個指標的擁有權。

### <a name="remarks"></a>備註

當`CAutoPtr`物件會採用指標的擁有權，則會自動刪除的指標和配置的任何資料時超出範圍。 如果[CAutoPtr::Detach](#detach)是呼叫，程式設計人員再次指定負責釋放任何配置的資源。

在偵錯組建中，如果，就會發生判斷提示失敗[CAutoPtr::m_p](#m_p)資料成員現在會指向現有的值; 也就是說，不等於 NULL。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

##  <a name="cautoptr"></a>  CAutoPtr::CAutoPtr

建構函式。

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
現有的指標。

*TSrc*<br/>
由另一個型別`CAutoPtr`，用來初始化目前的物件。

### <a name="remarks"></a>備註

`CAutoPtr`可以使用現有的指標建立物件，在此情況下傳送的是指標的擁有權。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

##  <a name="dtor"></a>  CAutoPtr::~CAutoPtr

解構函式。

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>備註

會釋放所有配置的資源。 呼叫[CAutoPtr::Free](#free)。

##  <a name="detach"></a>  CAutoPtr::Detach

呼叫此方法，以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回指標的複本。

### <a name="remarks"></a>備註

釋放指標的擁有權、 設定[CAutoPtr::m_p](#m_p)資料成員變數為 NULL，並傳回指標的複本。 之後呼叫`Detach`，它最多程式設計師可以釋放任何配置的資源，哪些`CAutoPtr`物件可能先前假設 reponsibility。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

##  <a name="free"></a>  CAutoPtr::Free

呼叫這個方法來刪除所指向的物件`CAutoPtr`。

```
void Free() throw();
```

### <a name="remarks"></a>備註

指向的物件`CAutoPtr`釋出，而[CAutoPtr::m_p](#m_p)資料成員變數會設為 NULL。

##  <a name="m_p"></a>  CAutoPtr::m_p

指標的資料成員變數中。

```
T* m_p;
```

### <a name="remarks"></a>備註

此成員變數會保留指標資訊。

##  <a name="operator_eq"></a>  CAutoPtr::operator =

指派運算子。

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>參數

*p*<br/>
變數的指標。

*TSrc*<br/>
類別型別。

### <a name="return-value"></a>傳回值

傳回的參考**CAutoPtr\< T >**。

### <a name="remarks"></a>備註

指派運算子會卸離`CAutoPtr`物件從目前的指標並附加新的指標*p*，在其位置。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

##  <a name="operator_ptr"></a>  CAutoPtr::operator -&gt;

成員指標運算子中。

```
T* operator->() const throw();
```

### <a name="return-value"></a>傳回值

傳回的值[CAutoPtr::m_p](#m_p)資料成員變數。

### <a name="remarks"></a>備註

使用這個運算子所指的類別中呼叫方法`CAutoPtr`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CAutoPtr`指向 NULL。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

##  <a name="operator_t_star"></a>  CAutoPtr::operator T*

轉換運算子。

```
operator T* () const throw();
```

### <a name="return-value"></a>傳回值

傳回類別範本中定義的物件資料類型的指標。

### <a name="example"></a>範例

請參閱中的範例[CAutoPtr 概觀](../../atl/reference/cautoptr-class.md)。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

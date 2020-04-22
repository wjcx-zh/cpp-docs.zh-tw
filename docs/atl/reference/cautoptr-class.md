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
ms.openlocfilehash: 2fa6eb26c2e2cd569d74c02d8303768b1aeb4f1c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748267"
---
# <a name="cautoptr-class"></a>CAutoPtr 類別

此類表示智慧指針對象。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

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
|[CAutoPtr:CAutoPtr](#cautoptr)|建構函式。|
|[CAutoPtr:_CAutoPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::附加](#attach)|調用此方法以獲取現有指標的擁有權。|
|[CAutoPtr::D塔奇](#detach)|調用此方法以釋放指標的擁有權。|
|[CAutoPtr:免費](#free)|呼叫此方法以移除指向的物件`CAutoPtr`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAutoPtr::操作員T*](#operator_t_star)|強制轉換運算符。|
|[CAutoPtr::運算符 |](#operator_eq)|分配運算符。|
|[CAutoPtr:運算符 ->](#operator_ptr)|指標到成員運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAutoPtr:m_p](#m_p)|指標數據成員變數。|

## <a name="remarks"></a>備註

此類提供創建和管理智慧指標的方法,通過在資源出鏡範圍時自動釋放資源,這將有助於防止記憶體洩漏。

此外,`CAutoPtr`複製構造函數和賦值運算元轉移指標的擁有權,將源指標複製到目標指標並將源指標設置為 NULL。 因此,不可能有兩`CAutoPtr`個物件每個存儲相同的指標,這減少了刪除同一指標兩次的可能性。

`CAutoPtr`還簡化了指標集合的創建。 與其派生集合類並重寫析構函數,不如創建`CAutoPtr`物件集合。 刪除集合時,`CAutoPtr`物件將超出範圍並自動刪除自身。

[CHeapPtr](../../atl/reference/cheapptr-class.md)和變體的工作方式`CAutoPtr`與 相同,只是它們使用不同的堆函數(而不是**C++新的**運算符和**刪除**運算符分配和釋放記憶體。 [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)`CAutoPtr`與 類似,唯一的區別是它使用**向量 new_** 和**向量刪除*** 來分配和釋放記憶體。

當需要陣列或智慧指標清單時,請參閱[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList。](../../atl/reference/cautoptrlist-class.md)

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::附加

調用此方法以獲取現有指標的擁有權。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
該`CAutoPtr`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

當物件`CAutoPtr`取得指標的擁有權時,當它超出範圍時,它將自動刪除指標和任何已分配的數據。 如果調用[CAutoPtr::Detach,](#detach)程式師將再次被賦予釋放任何分配資源的責任。

在調試生成中,如果[CAutoPtr::m_p](#m_p)數據成員當前指向現有值,則斷言失敗將發生;也就是說,它不等於 NULL。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr:CAutoPtr

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

*P*<br/>
現有指標。

*TSrc*<br/>
由另一個`CAutoPtr`管理的類型,用於初始化當前物件。

### <a name="remarks"></a>備註

可以使用`CAutoPtr`現有指標創建物件,在這種情況下,該對象會轉移指標的擁有權。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr:_CAutoPtr

解構函式。

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。 呼叫[CAutoPtr::免費](#free)。

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::D塔奇

調用此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

返回指標的副本。

### <a name="remarks"></a>備註

釋放指標的擁有權,將[CAutoPtr::m_p](#m_p)資料成員變數設置為 NULL,並返回指標的副本。 調用`Detach`後,由程式員`CAutoPtr`釋放 物件以前可能假定可重現的任何分配資源。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr:免費

呼叫此方法以移除指向的物件`CAutoPtr`。

```cpp
void Free() throw();
```

### <a name="remarks"></a>備註

釋放指向`CAutoPtr`的物件[,CAutoPtr::m_p](#m_p)資料成員變數設置為 NULL。

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr:m_p

指標數據成員變數。

```
T* m_p;
```

### <a name="remarks"></a>備註

此成員變數保存指標資訊。

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::運算符 |

分配運算符。

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>參數

*P*<br/>
指標。

*TSrc*<br/>
類類型。

### <a name="return-value"></a>傳回值

傳回**對 CAutoPtr\< T 的參考 >**。

### <a name="remarks"></a>備註

賦值運算符從任何當前`CAutoPtr`指標分離物件,並將新指標*p*將其附加在其位置。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr:運算子 -&gt;

指標到成員運算符。

```
T* operator->() const throw();
```

### <a name="return-value"></a>傳回值

返回[CAutoPtr::m_p](#m_p)數據成員變數的值。

### <a name="remarks"></a>備註

使用此運算符呼叫`CAutoPtr`物件指向的類中的方法。 在除錯產生中,如果指向 NULL,`CAutoPtr`則會發生斷言失敗。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::操作員T*

強制轉換運算符。

```
operator T* () const throw();
```

### <a name="return-value"></a>傳回值

返回指向類範本中定義的對象數據類型的指標。

### <a name="example"></a>範例

請參閱[CAutoPtr 概述](../../atl/reference/cautoptr-class.md)中的範例。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[C 自動向量Ptr 類別](../../atl/reference/cautovectorptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

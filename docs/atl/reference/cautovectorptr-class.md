---
title: C 自動向量Ptr 類別
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
ms.openlocfilehash: fc4bd4ba7a2f41a25679f1da718671f525519708
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748211"
---
# <a name="cautovectorptr-class"></a>C 自動向量Ptr 類別

此類表示使用向量新運算符和刪除運算符的智慧指針對象。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

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
|[C自動向量器:C自動向量器](#cautovectorptr)|建構函式。|
|[C自動向量器::*C自動向量Ptr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 自動向量器:分配](#allocate)|調用此方法以分配`CAutoVectorPtr`所指向的物件數組所需的記憶體。|
|[C自動向量器::附加](#attach)|調用此方法以獲取現有指標的擁有權。|
|[CAutoVectorPtr::Detach](#detach)|調用此方法以釋放指標的擁有權。|
|[CAutoVectorPtr:免費](#free)|呼叫此方法以移除指向的物件`CAutoVectorPtr`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtr:運算符 T |](#operator_t__star)|強制轉換運算符。|
|[CAutoVectorPtr::運算符 |](#operator_eq)|分配運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C自動向量器::m_p](#m_p)|指標數據成員變數。|

## <a name="remarks"></a>備註

此類提供創建和管理智慧指標的方法,通過在資源出鏡範圍時自動釋放資源,這將有助於防止記憶體洩漏。 `CAutoVectorPtr`與`CAutoPtr`類似 ,唯`CAutoVectorPtr`一的 區別是使用[向量新&#91;&#93;](../../standard-library/new-operators.md#op_new_arr)和[向量刪除&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr)分配和釋放記憶體,而不是C++**新的**和**刪除**運算符。 如果需要的收集類,`CAutoVectorPtr`請參閱[CAutoVectorPtr Element Traits。](../../atl/reference/cautovectorptrelementtraits-class.md)

有關使用智慧指標類的範例,請參閱[CAutoPtr。](../../atl/reference/cautoptr-class.md)

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>C 自動向量器:分配

調用此方法以分配`CAutoVectorPtr`所指向的物件數組所需的記憶體。

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>參數

*n 元素*<br/>
陣列中的項目數。

### <a name="return-value"></a>傳回值

如果記憶體成功分配,則返回 true,在失敗時為 false。

### <a name="remarks"></a>備註

在調試生成中,如果[CAutoVectorPtr::m_p](#m_p)成員變數當前指向現有值,則斷言失敗將發生;也就是說,它不等於 NULL。

## <a name="cautovectorptrattach"></a><a name="attach"></a>C自動向量器::附加

調用此方法以獲取現有指標的擁有權。

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
該`CAutoVectorPtr`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

當物件`CAutoVectorPtr`取得指標的擁有權時,當它超出範圍時,它將自動刪除指標和任何已分配的數據。 如果調用[CAutoVectorPtr::Detach,](#detach)程式師將再次被賦予釋放任何分配資源的責任。

在調試生成中,如果[CAutoVectorPtr::m_p](#m_p)成員變數當前指向現有值,則斷言失敗將發生;也就是說,它不等於 NULL。

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>C自動向量器:C自動向量器

建構函式。

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
現有指標。

### <a name="remarks"></a>備註

可以使用`CAutoVectorPtr`現有指標創建物件,在這種情況下,該對象會轉移指標的擁有權。

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>C自動向量器::*C自動向量Ptr

解構函式。

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。 呼叫[CAutoVectorPtr::免費](#free)。

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

調用此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

返回指標的副本。

### <a name="remarks"></a>備註

釋放指標的擁有權,將[CAutoVectorPtr::m_p](#m_p)成員變數設置為 NULL,並返回指標的副本。 調用`Detach`後,由程式員`CAutoVectorPtr`釋放 物件以前可能承擔的任何分配的資源。

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr:免費

呼叫此方法以移除指向的物件`CAutoVectorPtr`。

```cpp
void Free() throw();
```

### <a name="remarks"></a>備註

釋放`CAutoVectorPtr`下 指向的物件[,CAutoVectorPtr::m_p](#m_p)成員變數設置為 NULL。

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>C自動向量器::m_p

指標數據成員變數。

```
T* m_p;
```

### <a name="remarks"></a>備註

此成員變數保存指標資訊。

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::運算符 |

分配運算符。

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
指標。

### <a name="return-value"></a>傳回值

傳回對**CAutoVectorPtr\< T 的參考>**。

### <a name="remarks"></a>備註

賦值運算符從任何當前`CAutoVectorPtr`指標分離物件,並將新指標*p*將其附加在其位置。

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr:運算符 T |

強制轉換運算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

返回指向類範本中定義的對象數據類型的指標。

## <a name="see-also"></a>另請參閱

[CAutoPtr 類別](../../atl/reference/cautoptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

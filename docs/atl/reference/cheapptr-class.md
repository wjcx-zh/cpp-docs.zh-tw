---
title: CHeapPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326908"
---
# <a name="cheapptr-class"></a>CHeapPtr 類別

用於管理堆指標的智慧指標類。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在堆上的物件類型。

*配置器*<br/>
要使用的記憶體分配類。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeapPtr:CHeapPtr](#cheapptr)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeapPtr:分配](#allocate)|調用此方法以在堆上分配記憶體以存儲物件。|
|[CHeapPtr:重新分配](#reallocate)|調用此方法以重新分配堆上的記憶體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CHeapPtr::運算符 |](#operator_eq)|分配運算符。|

## <a name="remarks"></a>備註

`CHeapPtr`派生自[CHeapPtrBase,](../../atl/reference/cheapptrbase-class.md)預設使用 CRT 例程(在[CCRTAllocator)](../../atl/reference/ccrtallocator-class.md)來分配和釋放記憶體。 類[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可用於建構堆指標的清單。 另請參閱使用 COM 記憶體分配例程[的 CcomHeapPtr。](../../atl/reference/ccomheapptr-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr:分配

調用此方法以在堆上分配記憶體以存儲物件。

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>參數

*n 元素*<br/>
用於計算要分配的內存量的元素數。 預設值為 1。

### <a name="return-value"></a>傳回值

如果記憶體已成功分配,則返回 true,在失敗時為 false。

### <a name="remarks"></a>備註

分配器例程用於在堆上保留足夠的記憶體,以儲存構造函數中定義的類型的*nElement*物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr:CHeapPtr

建構函式。

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
現有堆指標或`CHeapPtr`。

### <a name="remarks"></a>備註

可以使用現有指標或`CHeapPtr`物件選擇創建堆指標。 如果是這樣,新`CHeapPtr`對象將負責管理新的指標和資源。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::運算符 |

指派運算子。

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
現有的 `CHeapPtr` 物件。

### <a name="return-value"></a>傳回值

返回對更新`CHeapPtr`的的引用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr:重新分配

調用此方法以重新分配堆上的記憶體。

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>參數

*n 元素*<br/>
用於計算要分配的內存量的新元素數。

### <a name="return-value"></a>傳回值

如果記憶體已成功分配,則返回 true,在失敗時為 false。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator 類](../../atl/reference/ccrtallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

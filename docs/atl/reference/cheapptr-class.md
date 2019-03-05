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
ms.openlocfilehash: 8cb35139e707d81a53edb762a2b7fc2ab41ff247
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296055"
---
# <a name="cheapptr-class"></a>CHeapPtr 類別

用來管理堆積指標的智慧型指標類別。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在堆積上的物件類型。

*Allocator*<br/>
要使用的記憶體配置類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|呼叫這個方法來儲存物件在堆積上配置記憶體。|
|[CHeapPtr::Reallocate](#reallocate)|呼叫這個方法來重新配置在堆積上的記憶體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`CHeapPtr` 衍生自[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) ，並預設使用的 CRT 常式 (在[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) 來配置和釋放記憶體。 此類別[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可用來建構清單的堆積指標。 另請參閱[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，它會使用 COM 記憶體配置常式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

呼叫這個方法來儲存物件在堆積上配置記憶體。

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>參數

*nElements*<br/>
用來計算配置的記憶體數量的項目數目。 預設值為 1。

### <a name="return-value"></a>傳回值

如果記憶體已成功，則傳回 true 配置失敗的 false。

### <a name="remarks"></a>備註

配置器常式用來保留足夠的記憶體來儲存堆積*nElement*物件的建構函式中定義的類型。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

建構函式。

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
現有的堆積指標或`CHeapPtr`。

### <a name="remarks"></a>備註

堆積指標可以選擇性地建立使用現有的指標，或`CHeapPtr`物件。 如果是的話，新`CHeapPtr`物件負責管理資源與新的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

指派運算子。

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
現有的 `CHeapPtr` 物件。

### <a name="return-value"></a>傳回值

傳回已更新的參考`CHeapPtr`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

呼叫這個方法來重新配置在堆積上的記憶體。

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>參數

*nElements*<br/>
新的用來計算配置的記憶體數量的項目數目。

### <a name="return-value"></a>傳回值

如果記憶體已成功，則傳回 true 配置失敗的 false。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator 類別](../../atl/reference/ccrtallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

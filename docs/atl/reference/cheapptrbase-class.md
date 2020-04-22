---
title: CHeapPtrBase 類別
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: e247b4f488411ffdcde5d1d9016436c9c36fe793
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747689"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 類別

此類是多個智慧堆指標類的基礎。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在堆上的物件類型。

*配置器*<br/>
要使用的記憶體分配類。 默認情況下,CRT 例程用於分配和釋放記憶體。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeapPtrBase:_CHeapPtrBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeapPtrBase:配置位元組](#allocatebytes)|調用此方法以分配記憶體。|
|[CHeapPtrBase:附加](#attach)|調用此方法以獲取現有指標的擁有權。|
|[CHeapPtrBase::D](#detach)|調用此方法以釋放指標的擁有權。|
|[CHeapPtrBase:免費](#free)|呼叫此方法以移除指向的物件`CHeapPtrBase`。|
|[CHeapPtrBase::重新分配位元組](#reallocatebytes)|調用此方法重新分配記憶體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CHeapPtrBase:運算符 T*](#operator_t_star)|強制轉換運算符。|
|[CHeapPtrBase:運算符&](#operator_amp)|& 運算子。|
|[CHeapPtrBase::運算符 ->](#operator_ptr)|指標到成員運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CHeapPtrBase:m_pData](#m_pdata)|指標數據成員變數。|

## <a name="remarks"></a>備註

此類是多個智慧堆指標類的基礎。 派生類(例如[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CComHeapPtr)](../../atl/reference/ccomheapptr-class.md)添加自己的構造函數和運算符。 有關實現示例,請參閱這些類。

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase:配置位元組

調用此方法以分配記憶體。

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要分配的記憶體位元組數。

### <a name="return-value"></a>傳回值

如果已成功分配記憶體,則返回 true,否則為 false。

### <a name="remarks"></a>備註

在調試生成中,如果[CHeapPtrBase::m_pData](#m_pdata)成員變數當前指向現有值,則斷言失敗將發生;也就是說,它不等於 NULL。

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase:附加

調用此方法以獲取現有指標的擁有權。

```cpp
void Attach(T* pData) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
該`CHeapPtrBase`物件將取得此指標的擁有權。

### <a name="remarks"></a>備註

當物件`CHeapPtrBase`取得指標的擁有權時,當它超出範圍時,它將自動刪除指標和任何已分配的數據。

在調試生成中,如果[CHeapPtrBase::m_pData](#m_pdata)成員變數當前指向現有值,則斷言失敗將發生;也就是說,它不等於 NULL。

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase:_CHeapPtrBase

解構函式。

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::D

調用此方法以釋放指標的擁有權。

```
T* Detach() throw();
```

### <a name="return-value"></a>傳回值

返回指標的副本。

### <a name="remarks"></a>備註

釋放指標的擁有權,將[CHeapPtrBase::m_pData](#m_pdata)成員變數設置為 NULL,並返回指標的副本。

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase:免費

呼叫此方法以移除指向的物件`CHeapPtrBase`。

```cpp
void Free() throw();
```

### <a name="remarks"></a>備註

釋放`CHeapPtrBase`下 指向的物件[,CHeapPtrBase:m_pData](#m_pdata)成員變數設定為 NULL。

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase:m_pData

指標數據成員變數。

```
T* m_pData;
```

### <a name="remarks"></a>備註

此成員變數保存指標資訊。

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::運算子&amp;

& 運算子。

```
T** operator&() throw();
```

### <a name="return-value"></a>傳回值

傳回物件指向的物件的`CHeapPtrBase`位址 。

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase:運算子 -&gt;

指標到成員運算符。

```
T* operator->() const throw();
```

### <a name="return-value"></a>傳回值

返回[CHeapPtrBase:m_pData](#m_pdata)成員變數的值。

### <a name="remarks"></a>備註

使用此運算符呼叫`CHeapPtrBase`物件指向的類中的方法。 在除錯產生中,如果指向 NULL,`CHeapPtrBase`則會發生斷言失敗。

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase:運算符 T*

強制轉換運算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>備註

傳[回 CHeapPtrBase:m_pData](#m_pdata)。

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase::重新分配位元組

調用此方法重新分配記憶體。

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要分配的新內存量(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果已成功分配記憶體,則返回 true,否則為 false。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

---
title: IAccessorImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: f1865089100ac7f60e8c011e72eedb3d0a3f8470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447069"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 類別

提供[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>參數

*T*<br/>
您的資料列集或命令物件類別。

*BindType*<br/>
系結資訊的儲存單位。 預設值為 `ATLBINDINGS` 結構（請參閱為 atldb.h）。

*BindingVector*<br/>
資料行資訊的儲存單位。 預設值是[CAtlMap](../../atl/reference/catlmap-class.md) ，其中 key 元素是 HACCESSOR 值，而 value 元素是 `BindType` 結構的指標。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|建構函式。|

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|將參考次數 (Reference Count) 加入至現有的存取子 (Accessor)。|
|[CreateAccessor](#createaccessor)|透過一組繫結建立存取子。|
|[GetBindings](#getbindings)|傳回存取子中的繫結。|
|[ReleaseAccessor](#releaseaccessor)|釋放存取子。|

## <a name="remarks"></a>備註

這在資料列集和命令上是必要的。 OLE DB 需要提供者來執行 HACCESSOR，這是[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))結構陣列的標記。 `IAccessorImpl` 提供的 HACCESSORs 是 `BindType` 結構的位址。 根據預設，`BindType` 會定義為 `IAccessorImpl`的範本定義中的 `ATLBINDINGS`。 `BindType` 提供一個機制，供 `IAccessorImpl` 用來追蹤其 `DBBINDING` 陣列中的元素數目，以及參考計數和存取子旗標。

## <a name="iaccessorimpl"></a>IAccessorImpl：： IAccessorImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a>IAccessorImpl：： AddRefAccessor

將參考次數 (Reference Count) 加入至現有的存取子 (Accessor)。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IAccessor：： AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) 。

## <a name="createaccessor"></a>IAccessorImpl：： CreateAccessor

透過一組繫結建立存取子。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IAccessor：： CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) 。

## <a name="getbindings"></a>IAccessorImpl：： GetBindings

在存取子中，傳回取用者的基本資料行系結。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IAccessor：： GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) 。

## <a name="releaseaccessor"></a>IAccessorImpl：： ReleaseAccessor

釋放存取子。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IAccessor：： ReleaseAccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
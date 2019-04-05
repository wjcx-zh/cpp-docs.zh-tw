---
title: IAccessorImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
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
ms.openlocfilehash: a4f98cdfea9ea1e82ec0a3de09e292604a6c199f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032111"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 類別

提供實作[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>參數

*T*<br/>
您的資料列集或指令的物件類別。

*BindType*<br/>
存放裝置的繫結資訊。 預設值是`ATLBINDINGS`結構 （請參閱為 atldb.h）。

*BindingVector*<br/>
資料行資訊的儲存體單位。 預設值是[CAtlMap](../../atl/reference/catlmap-class.md)其中的索引鍵的項目是 HACCESSOR 的值，而值的項目是指標`BindType`結構。

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
|[AddRefAccessor](#addrefaccessor)|將現有的存取子中的參考計數。|
|[CreateAccessor](#createaccessor)|從一組繫結建立存取子。|
|[GetBindings](#getbindings)|傳回的繫結的存取子中。|
|[ReleaseAccessor](#releaseaccessor)|釋放存取子。|

## <a name="remarks"></a>備註

這是資料列集和命令的必要參數。 OLE DB 會要求提供者實作 HACCESSOR，這是標記的陣列[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))結構。 所提供的 HACCESSORs`IAccessorImpl`是位址`BindType`結構。 根據預設，`BindType`指`ATLBINDINGS`在`IAccessorImpl`的範本定義。 `BindType` 提供所使用的機制`IAccessorImpl`追蹤中的項目數其`DBBINDING`陣列以及參考計數和存取子旗標。

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

將現有的存取子中的參考計數。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>參數

請參閱[IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

從一組繫結建立存取子。

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

請參閱[iaccessor:: Createaccessor](/previous-versions/windows/desktop/ms720969(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="getbindings"></a> IAccessorImpl::GetBindings

從存取子中取用者會傳回基本的資料行繫結。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>參數

請參閱[IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

釋放存取子。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>參數

請參閱[iaccessor:: Releaseaccessor](/previous-versions/windows/desktop/ms719717(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)
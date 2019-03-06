---
title: ICommandImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: e1f461cc850a2122af7902babfad8f1e14ac3e33
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424843"
---
# <a name="icommandimpl-class"></a>ICommandImpl 類別

提供實作[ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`ICommandImpl`。

*CommandBase*<br/>
命令介面。 預設為 `ICommand`。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[取消](#cancel)|取消目前執行的命令。|
|[CancelExecution](#cancelexecution)|取消目前執行的命令。|
|[CreateRowset](#createrowset)|建立資料列集物件。|
|[Execute](#execute)|執行命令。|
|[GetDBSession](#getdbsession)|傳回建立命令的工作階段的介面指標。|
|[ICommandImpl](#icommandimpl)|建構函式。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bCancel](#bcancel)|指出命令是否已取消。|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|指出命令是否要取消執行時。|
|[m_bIsExecuting](#bisexecuting)|表示命令目前是否正在執行。|

## <a name="remarks"></a>備註

Command 物件上的強制介面。

## <a name="cancel"></a> Icommandimpl:: Cancel

取消目前執行的命令。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>備註

請參閱[ICommand::Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="cancelexecution"></a> Icommandimpl:: Cancelexecution

取消目前執行的命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> ICommandImpl::CreateRowset

由呼叫[Execute](../../data/oledb/icommandimpl-execute.md)建立單一資料列集。

### <a name="syntax"></a>語法

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>參數

*RowsetClass*<br/>
代表使用者的資料列集類別的樣板類別成員。 通常是由精靈產生。

*pUnkOuter*<br/>
[in]指標，控制`IUnknown`介面資料列集建立為彙總的一部分，否則為 null。

*riid*<br/>
[in]對應至*riid*在`ICommand::Execute`。

*pParams*<br/>
[輸入/輸出]對應至*pParams*在`ICommand::Execute`。

*pcRowsAffected*<br/>
對應至*pcRowsAffected*在`ICommand::Execute`。

*ppRowset*<br/>
[輸入/輸出]對應至*Pprowset&lt*在`ICommand::Execute`。

*pRowsetObj*<br/>
[out]資料列集物件的指標。 通常不會使用此參數，但如果您必須在資料列集上執行更多工作，再將它傳遞至 COM 物件可以使用它。 存留期*pRowsetObj*繫結*Pprowset&lt*。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。 請參閱`ICommand::Execute`如需一般值的清單。

### <a name="remarks"></a>備註

若要建立多個資料列集，或提供您自己的建立不同的資料列集的條件，將不同的呼叫置於`CreateRowset`內在`Execute`。

請參閱[icommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85))在*OLE DB 程式設計人員參考。*

## <a name="execute"></a> Icommandimpl:: Execute

執行命令。

### <a name="syntax"></a>語法

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>參數

請參閱[icommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85))中*OLE DB 程式設計人員參考*。

### <a name="remarks"></a>備註

要求的連出介面將會取得從這個函式建立的資料列集物件介面。

`Execute` 呼叫[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。 若要建立多個資料列集，或提供您自己的條件，來建立不同的資料列集的預設實作會覆寫。

## <a name="getdbsession"></a> Icommandimpl:: Getdbsession

傳回建立命令的工作階段的介面指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>參數

請參閱[ICommand::GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85))中*OLE DB 程式設計人員參考*。

### <a name="remarks"></a>備註

適用於從工作階段中擷取屬性。

## <a name="icommandimpl"></a> Icommandimpl:: Icommandimpl

建構函式。

### <a name="syntax"></a>語法

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> ICommandImpl::m_bCancel

指出是否可以取消命令為止。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>備註

您可以擷取中的這個變數`Execute`命令類別和適當的取消方法。

## <a name="bcancelwhenexecuting"></a> Icommandimpl:: M_bcancelwhenexecuting

指出執行時，是否可以取消命令。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>備註

預設值為 **，則為 true** （可取消）。

## <a name="bisexecuting"></a> Icommandimpl:: M_bisexecuting

表示命令目前是否正在執行。

### <a name="syntax"></a>語法

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>備註

`Execute`命令類別的方法可以將這個變數設 **，則為 true**。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
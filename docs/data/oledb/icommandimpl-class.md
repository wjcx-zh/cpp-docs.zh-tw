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
ms.openlocfilehash: 6e095e01d3131f98b44935705b2564291fb13844
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447057"
---
# <a name="icommandimpl-class"></a>ICommandImpl 類別

提供[ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `ICommandImpl`的類別。

*CommandBase*<br/>
命令介面。 預設值為 `ICommand`。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[取消](#cancel)|取消目前的命令執行。|
|[CancelExecution](#cancelexecution)|取消目前的命令執行。|
|[CreateRowset](#createrowset)|建立資料列集物件。|
|[執行](#execute)|執行命令。|
|[GetDBSession](#getdbsession)|傳回建立命令之會話的介面指標。|
|[ICommandImpl](#icommandimpl)|建構函式。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bCancel](#bcancel)|指出是否要取消命令。|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|指出執行時是否要取消命令。|
|[m_bIsExecuting](#bisexecuting)|指出命令目前是否正在執行。|

## <a name="remarks"></a>備註

命令物件上的強制介面。

## <a name="cancel"></a>ICommandImpl：： Cancel

取消目前的命令執行。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>備註

請參閱 OLE DB 程式設計*人員參考*中的[ICommand：： Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) 。

## <a name="cancelexecution"></a>ICommandImpl：： CancelExecution

取消目前的命令執行。

### <a name="syntax"></a>語法

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a>ICommandImpl：： CreateRowset

由[Execute](../../data/oledb/icommandimpl-execute.md)呼叫以建立單一資料列集。

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
範本類別成員，代表使用者的資料列集類別。 通常由 wizard 產生。

*pUnkOuter*<br/>
在如果將資料列集建立為匯總的一部分，則為控制 `IUnknown` 介面的指標;否則，它會是 null。

*riid*<br/>
在對應至 `ICommand::Execute`中的*riid* 。

*pParams*<br/>
[in/out]對應至 `ICommand::Execute`中的*pParams* 。

*pcRowsAffected*<br/>
對應至 `ICommand::Execute`中的*pcRowsAffected* 。

*ppRowset*<br/>
[in/out]對應至 `ICommand::Execute`中的*ppRowset* 。

*pRowsetObj*<br/>
脫銷資料列集物件的指標。 通常不會使用這個參數，但如果您必須在資料列集上執行更多工做，然後才將它傳遞至 COM 物件，則可以使用此參數。 *PRowsetObj*的存留期是由*ppRowset*所系結。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。 如需一般值的清單，請參閱 `ICommand::Execute`。

### <a name="remarks"></a>備註

若要建立一個以上的資料列集，或提供您自己的條件來建立不同的資料列集，請從 `Execute`內，將不同的呼叫放在 `CreateRowset`。

請參閱 OLE DB 程式設計*人員參考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

## <a name="execute"></a>ICommandImpl：： Execute

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

請參閱 OLE DB 程式設計*人員參考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

### <a name="remarks"></a>備註

所要求的輸出介面將是從這個函式所建立的資料列集物件取得的介面。

`Execute` 會呼叫[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。 覆寫預設的實作為建立多個資料列集，或提供您自己的條件來建立不同的資料列集。

## <a name="getdbsession"></a>ICommandImpl：： GetDBSession

傳回建立命令之會話的介面指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommand：： GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) 。

### <a name="remarks"></a>備註

適用于從會話抓取屬性。

## <a name="icommandimpl"></a>ICommandImpl：： ICommandImpl

建構函式。

### <a name="syntax"></a>語法

```cpp
ICommandImpl();
```

## <a name="bcancel"></a>ICommandImpl：： m_bCancel

指出是否已取消命令。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>備註

您可以在命令類別的 `Execute` 方法中取出此變數，並視需要取消。

## <a name="bcancelwhenexecuting"></a>ICommandImpl：： m_bCancelWhenExecuting

指出執行時是否可以取消命令。

### <a name="syntax"></a>語法

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>備註

預設值為**true** （可以取消）。

## <a name="bisexecuting"></a>ICommandImpl：： m_bIsExecuting

指出命令目前是否正在執行。

### <a name="syntax"></a>語法

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>備註

命令類別的 `Execute` 方法可以將此變數設定為**true**。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
---
title: IRowsetNotifyImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: f938d9e92bc2f447ecfa82f2bfb27c8fda7652ab
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845103"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 類別

在取用者上執行和註冊 [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) ， (也稱為「接收器」 ) 讓它可以處理通知。

## <a name="syntax"></a>語法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[OnFieldChange](#onfieldchange)|告知消費者，資料行值的任何變更。|
|[OnRowChange](#onrowchange)|告知消費者，資料列的第一個變更或影響整個資料列的任何變更。|
|[OnRowsetChange](#onrowsetchange)|告知消費者，影響整個資料列集的任何變更。|

## <a name="remarks"></a>備註

請參閱接收在取用者上執行連接點介面的 [通知](../../data/oledb/receiving-notifications.md) 。

`IRowsetNotifyImpl` 提供的虛擬實作為 `IRowsetNotify` ，具有 `IRowsetNotify` [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))、 [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))和 [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))方法的空白函式。 如果您在執行介面時繼承自這個類別 `IRowsetNotify` ，您可以只執行所需的方法。 您也需要自行為其他方法提供空白的實作為。

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyImpl：： OnFieldChange

告知消費者，資料行值的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>參數

如需參數描述，請參閱 [IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱 [IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝 [IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a> IRowsetNotifyImpl：： OnRowChange

告知消費者，資料列的第一個變更或影響整個資料列的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>參數

如需參數描述，請參閱 [IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱 [IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝 [IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyImpl：： OnRowsetChange

告知消費者，影響整個資料列集的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>參數

如需參數描述，請參閱 [IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱 [IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝 [IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
[IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)

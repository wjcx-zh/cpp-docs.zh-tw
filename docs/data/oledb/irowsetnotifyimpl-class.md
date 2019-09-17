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
ms.openlocfilehash: 4e6b4c3298c063038e7365496f26f50d3789be86
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311756"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 類別

在取用者上執行並註冊[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) （也稱為「接收」），讓它可以處理通知。

## <a name="syntax"></a>語法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[OnFieldChange](#onfieldchange)|通知取用者對資料行值的任何變更。|
|[OnRowChange](#onrowchange)|通知取用者第一次變更資料列或任何影響整個資料列的變更。|
|[OnRowsetChange](#onrowsetchange)|通知取用者影響整個資料列集的任何變更。|

## <a name="remarks"></a>備註

請參閱接收有關在取用者上執行連接點介面的[通知](../../data/oledb/receiving-notifications.md)。

`IRowsetNotifyImpl`提供的虛擬實作為`IRowsetNotify`，方法為[OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))、[OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) `IRowsetNotify`和[OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))的空白函數。 如果您在執行`IRowsetNotify`介面時繼承自這個類別，則只能執行所需的方法。 您也必須為其他方法自行提供空的執行方式。

## <a name="onfieldchange"></a>IRowsetNotifyImpl：： OnFieldChange

通知取用者對資料行值的任何變更。

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

如需參數描述，請參閱[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="onrowchange"></a>IRowsetNotifyImpl：： OnRowChange

通知取用者第一次變更資料列或任何影響整個資料列的變更。

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

如需參數描述，請參閱[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="onrowsetchange"></a>IRowsetNotifyImpl：： OnRowsetChange

通知取用者影響整個資料列集的任何變更。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>參數

如需參數描述，請參閱[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如需傳回值的描述，請參閱[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

### <a name="remarks"></a>備註

這個方法會包裝[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) 
 [IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)

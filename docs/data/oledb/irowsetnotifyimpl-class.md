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
ms.openlocfilehash: 01bcc60b0c88a3953d5e75b53ac58877f7eb15df
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556383"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 類別

實作並註冊[IRowsetNotify](https://docs.microsoft.com/previous-versions/windows/desktop/ms712959(v=vs.85))上取用者 （也稱為 「 接收 」），使其可以處理通知。

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
|[OnFieldChange](#onfieldchange)|告知消費者的資料行值的任何變更。|
|[OnRowChange](#onrowchange)|告知消費者，資料列的第一個變更或影響整個資料列的任何變更。|
|[OnRowsetChange](#onrowsetchange)|通知任何變更會影響整個資料列集取用的者。|

## <a name="remarks"></a>備註

請參閱[接收通知](../../data/oledb/receiving-notifications.md)需於取用者實作連接點介面。

`IRowsetNotifyImpl` 提供的虛擬實作`IRowsetNotify`，使用空白的函式`IRowsetNotify`方法[OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85))， [OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85))，和[OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)). 如果您繼承自這個類別實作時`IRowsetNotify`介面，您可以實作只有您所需的方法。 您也需要自行提供空的實作，如需其他方法。

## <a name="onfieldchange"></a> Irowsetnotifyimpl:: Onfieldchange

告知消費者的資料行值的任何變更。

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

請參閱[IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85))的參數說明。

### <a name="return-value"></a>傳回值

請參閱[IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85))的回傳值描述。

### <a name="remarks"></a>備註

這個方法會包裝[IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="onrowchange"></a> Irowsetnotifyimpl:: Onrowchange

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

請參閱[irowsetnotify:: Onrowchange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85))的參數說明。

### <a name="return-value"></a>傳回值

請參閱[irowsetnotify:: Onrowchange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85))的回傳值描述。

### <a name="remarks"></a>備註

這個方法會包裝[irowsetnotify:: Onrowchange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="onrowsetchange"></a> Irowsetnotifyimpl:: Onrowsetchange

通知任何變更會影響整個資料列集取用的者。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>參數

請參閱[IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85))的參數說明。

### <a name="return-value"></a>傳回值

請參閱[IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85))的回傳值描述。

### <a name="remarks"></a>備註

這個方法會包裝[IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85))方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](https://docs.microsoft.com/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)
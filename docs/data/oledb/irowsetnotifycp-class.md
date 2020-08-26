---
title: IRowsetNotifyCP 類別
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: 2f8c80570e4771d1b0e713083f64bc982ddb9009
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840280"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 類別

針對連接點介面 [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))，執行提供者網站。

## <a name="syntax"></a>語法

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IRowsetNotifyCP` 。

*ReentrantEventSync*<br/>
支援重新進入 (預設值的 mutex 類別 `CComSharedMutex`) 。 Mutex 是一種同步處理物件，可讓某個執行緒對資源進行互斥的存取。

*piid*<br/>
連接點介面的介面識別碼指標 (`IID*`) `IRowsetNotify` 。 預設值是 `&__uuidof(IRowsetNotify)`。

*DynamicUnkArray*<br/>
[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)類型的陣列，此陣列是 `IUnknown` 用戶端接收介面指標的動態配置陣列。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|通知取用者變更資料行的值。|
|[Fire_OnRowChange](#onrowchange)|通知取用者影響資料列的變更。|
|[Fire_OnRowsetChange](#onrowsetchange)|通知取用者影響整個資料列集的變更。|

## <a name="remarks"></a>備註

`IRowsetNotifyCP` 會在資料列集內容變更的連接點上，執行廣播功能以建議接聽程式 `IID_IRowsetNotify` 。

請注意，您也必須在取用 `IRowsetNotify` 者上執行和註冊 (也稱為「接收器」 ) 使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，讓取用者可以處理通知。 請參閱接收在取用者上執行連接點介面的 [通知](../../data/oledb/receiving-notifications.md) 。

如需有關如何執行通知的詳細資訊，請參閱 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)中的「支援通知」。

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a> IRowsetNotifyCP：： Fire_OnFieldChange

廣播 [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 事件，以通知取用者變更資料行的值。

### <a name="syntax"></a>語法

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetNotify：： OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) 。

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a> IRowsetNotifyCP：： Fire_OnRowChange

將 [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 事件廣播到連接點上的所有接聽程式 `IID_IRowsetNotify` ，以通知取用者影響資料列的變更。

### <a name="syntax"></a>語法

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetNotify：： OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) 。

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a> IRowsetNotifyCP：： Fire_OnRowsetChange

將 [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 事件廣播到連接點上的所有接聽程式 `IID_IRowsetNotify` ，以通知取用者影響整個資料列集的變更。

### <a name="syntax"></a>語法

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetNotify：： OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[COM)  (通知 ](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)

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
ms.openlocfilehash: 481c2c0ec28972e9cef8d1103e49afa2037c2393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311813"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 類別

執行連接點介面[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))的提供者網站。

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
衍生自`IRowsetNotifyCP`的類別。

*ReentrantEventSync*<br/>
支援重新進入的 mutex 類別（預設值為`CComSharedMutex`）。 Mutex 是一種同步處理物件，可讓一個執行緒對資源進行互斥的存取。

*piid*<br/>
連接點介面的介面`IID*`識別碼指標（）。 `IRowsetNotify` 預設值為 `&__uuidof(IRowsetNotify)`。

*DynamicUnkArray*<br/>
[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)類型的陣列，這是動態配置的用戶端接收`IUnknown`介面指標陣列。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|通知取用者對資料行值的變更。|
|[Fire_OnRowChange](#onrowchange)|通知取用者影響資料列的變更。|
|[Fire_OnRowsetChange](#onrowsetchange)|通知取用者影響整個資料列集的變更。|

## <a name="remarks"></a>備註

`IRowsetNotifyCP`會執行廣播函式，以通知資料列`IID_IRowsetNotify`集內容變更連接點上的接聽程式。

請注意，您也必須使用`IRowsetNotify` [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，在取用者（也稱為「接收器」）上執行並註冊，讓取用者可以處理通知。 請參閱接收有關在取用者上執行連接點介面的[通知](../../data/oledb/receiving-notifications.md)。

如需有關如何執行通知的詳細資訊，請參閱[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)中的「支援通知」。

## <a name="onfieldchange"></a>IRowsetNotifyCP：： Fire_OnFieldChange

廣播[OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85))事件，以通知取用者變更資料行的值。

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

## <a name="onrowchange"></a>IRowsetNotifyCP：： Fire_OnRowChange

將[OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))事件廣播到連接點`IID_IRowsetNotify`上的所有接聽程式，以通知取用者影響資料列的變更。

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

## <a name="onrowsetchange"></a>IRowsetNotifyCP：： Fire_OnRowsetChange

將[OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85))事件廣播到連接點`IID_IRowsetNotify`上的所有接聽程式，以通知取用者影響整個資料列集的變更。

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
[通知（COM）](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)
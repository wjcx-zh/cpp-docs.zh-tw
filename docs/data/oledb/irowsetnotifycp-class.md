---
title: IRowsetNotifyCP 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: efd643414085ee71c48e3d4a5654dac82b74b030
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081283"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 類別

實作連接點介面的提供者站台[IRowsetNotify](/previous-versions/windows/desktop/ms712959)。

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
類別衍生自`IRowsetNotifyCP`。

*ReentrantEventSync*<br/>
支援重新進入的 mutex 類別 (預設值是`CComSharedMutex`)。 Mutex 是同步處理物件，可讓一個執行緒互斥資源的存取權。

*piid*<br/>
介面識別碼指標 (`IID*`) 的`IRowsetNotify`連接點的介面。 預設值是 `&__uuidof(IRowsetNotify)`。

*DynamicUnkArray*<br/>
類型的陣列[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，這是動態配置的陣列的`IUnknown`指標給用戶端接收器介面。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|告知消費者的資料行的值變更。|
|[Fire_OnRowChange](#onrowchange)|告知消費者，影響資料列的變更。|
|[Fire_OnRowsetChange](#onrowsetchange)|告知消費者，影響整個資料列集的變更。|

## <a name="remarks"></a>備註

`IRowsetNotifyCP` 實作廣播通知接聽程式連接點上的函式`IID_IRowsetNotify`的資料列集的內容變更。

請注意，您也必須實作並註冊`IRowsetNotify`在取用者 （也稱為 「 接收 」） 使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，好讓取用者可以處理通知。 請參閱[接收通知](../../data/oledb/receiving-notifications.md)需於取用者實作連接點介面。

實作通知的詳細資訊，請參閱 「 支援通知 」，在[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)。

## <a name="onfieldchange"></a> Irowsetnotifycp:: Fire_onfieldchange

廣播[OnFieldChange](/previous-versions/windows/desktop/ms715961)事件來通知取用者的資料行的值變更。

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

請參閱[IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961)中*OLE DB 程式設計人員參考*。

## <a name="onrowchange"></a> Irowsetnotifycp:: Fire_onrowchange

廣播[OnRowChange](/previous-versions/windows/desktop/ms722694)事件，以連接點上的所有接聽程式`IID_IRowsetNotify`來通知取用者的變更會影響資料列。

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

請參閱[irowsetnotify:: Onrowchange](/previous-versions/windows/desktop/ms722694)中*OLE DB 程式設計人員參考*。

## <a name="onrowsetchange"></a> Irowsetnotifycp:: Fire_onrowsetchange

廣播[OnRowsetChange](/previous-versions/windows/desktop/ms722669)事件，以連接點上的所有接聽程式`IID_IRowsetNotify`來通知取用者的變更會影響整個資料列集。

### <a name="syntax"></a>語法

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>參數

請參閱[IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669)中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[通知 (COM)](/windows/desktop/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)
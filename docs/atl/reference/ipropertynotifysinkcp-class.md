---
title: IPropertyNotifySinkCP 類
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329602"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 類

此類將[IProperty Notify Sink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面公開為可連接物件上的傳出介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPropertyNotifySinkCP`。

*CDV*<br/>
管理連接點與其接收器之間的連接的類。 默認值為[CComDynamicUnkarray,](../../atl/reference/ccomdynamicunkarray-class.md)它允許無限制的連接。 您還可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md),它指定固定數量的連接。

## <a name="remarks"></a>備註

`IPropertyNotifySinkCP`通過其基類[IConnectionPointImpl 繼承](../../atl/reference/iconnectionpointimpl-class.md)所有方法。

[IProperty NotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)介面允許接收器物件接收有關屬性更改的通知。 類`IPropertyNotifySinkCP`公開此介面作為可連接物件上的傳出介面。 客戶端必須在接收器上`IPropertyNotifySink`實現方法。

從`IPropertyNotifySinkCP`要創建`IPropertyNotifySink`表示 介面的連接點時派生類。

有關在 ATL 中使用連接點的詳細資訊,請參閱文章[連接點](../../atl/atl-connection-points.md)。

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="see-also"></a>另請參閱

[IConnectionPointimpl 類別](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPoint容器Impl類](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

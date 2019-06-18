---
title: ISupportErrorInfoImpl 類別
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141709"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl 類別

這個類別提供的預設實作[ISupportErrorInfo 介面](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)方法，可以用於只有單一介面產生物件錯誤時。

> [!IMPORTANT]
> 此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>參數

*piid*<br/>
支援介面的 IID 的指標[IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指出介面是否由識別`riid`支援[IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)介面。|

## <a name="remarks"></a>備註

[ISupportErrorInfo 介面](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)可確保資訊時發生錯誤，可以傳回給用戶端。 物件，使用`IErrorInfo`必須實作`ISupportErrorInfo`。

類別`ISupportErrorInfoImpl`提供的預設實作`ISupportErrorInfo`方法，可以用於只有單一介面產生物件錯誤時。 例如:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

指出介面是否由識別`riid`支援[IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)介面。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>備註

請參閱[ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

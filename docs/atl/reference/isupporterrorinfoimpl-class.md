---
title: Isupporterrorinfoimpl 當成基類類別
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
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495368"
---
# <a name="isupporterrorinfoimpl-class"></a>Isupporterrorinfoimpl 當成基類類別

這個類別會提供[ISupportErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)的預設實值, 而且可以在只有單一介面產生物件錯誤時使用。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>參數

*piid*<br/>
支援[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)之介面的 IID 指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|指出所識別`riid`的介面是否支援[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)介面。|

## <a name="remarks"></a>備註

[ISupportErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)可確保錯誤資訊可以傳回至用戶端。 使用`IErrorInfo`的物件必須執行`ISupportErrorInfo`。

類別`ISupportErrorInfoImpl`提供的預設`ISupportErrorInfo`執行, 而且可以在只有單一介面產生物件錯誤時使用。 例如：

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

指出所識別`riid`的介面是否支援[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)介面。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) 。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)

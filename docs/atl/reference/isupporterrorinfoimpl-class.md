---
title: ISupportErrorInfoimpl 課程
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
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326371"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoimpl 課程

此類提供[ISupportErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)的預設實現,當只有一個介面在物件上生成錯誤時,可以使用。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>參數

*皮伊德*<br/>
指向支援[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)的介面的 IID 的指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ISupportErrorinfoimpl::介面支援錯誤資訊](#interfacesupportserrorinfo)|指示由`riid`[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)介面標識的介面是否支援。|

## <a name="remarks"></a>備註

[ISupportErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo)可確保可以將錯誤資訊返回到用戶端。 使用`IErrorInfo`物件必須實作`ISupportErrorInfo`。

類別`ISupportErrorInfoImpl`提供的`ISupportErrorInfo`預設實現,當只有一個介面在物件上產生錯誤時可以使用 。 例如：

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorinfoimpl::介面支援錯誤資訊

指示由`riid`[IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)介面標識的介面是否支援。

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>備註

請參閱[ISupportErrorInfo:介面支援 Windows](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) SDK 中的錯誤資訊。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)

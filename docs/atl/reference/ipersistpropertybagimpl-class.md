---
title: IPersist財產巴格普普類
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326489"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersist財產巴格普普類

此類實現`IUnknown`並允許物件將其屬性保存到用戶端提供的屬性包。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPersistPropertyBagImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 堅持屬性巴格::獲取類 ID](#getclassid)|檢索物件的 CLSID。|
|[我堅持財產巴格普::INIT新](#initnew)|初始化新創建的物件。 ATL 實現返回S_OK。|
|[IPersist 屬性袋::載入](#load)|從用戶端提供的屬性包載入物件的屬性。|
|[IPersist屬性袋::儲存](#save)|將物件的屬性保存到用戶端提供的屬性包中。|

## <a name="remarks"></a>備註

[IPersist PropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\))介面允許物件將其屬性保存到用戶端提供的屬性包。 類`IPersistPropertyBagImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

`IPersistPropertyBag`與[IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\))和[IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\))一起使用。 后兩個介面必須由客戶端實現。 通過`IPropertyBag`,用戶端保存並載入物件的單個屬性。 通過`IErrorLog`,物件和用戶端都可以報告遇到的任何錯誤。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>I 堅持屬性巴格::獲取類 ID

檢索物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱[IPersist:在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中獲取 ClassID。

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>我堅持財產巴格普::INIT新

初始化新創建的物件。

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IPersist 屬性袋::Windows](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) SDK 中的「新」。。

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersist 屬性袋::載入

從用戶端提供的屬性包載入物件的屬性。

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射來檢索此資訊。

請參閱[IPersist 屬性袋::](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\))在 Windows SDK 中載入。

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersist屬性袋::儲存

將物件的屬性保存到用戶端提供的屬性包中。

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射來存儲此資訊。 默認情況下,此方法保存所有屬性,而不考慮*fSaveAllProperties*的值。

請參閱[IPersist 屬性袋::保存在](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\))Windows SDK 中。

## <a name="see-also"></a>另請參閱

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)

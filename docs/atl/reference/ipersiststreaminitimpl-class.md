---
title: I 堅持流內普普類
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326453"
---
# <a name="ipersiststreaminitimpl-class"></a>I 堅持流內普普類

此類實現`IUnknown`並提供[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPersistStreamInitImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 堅持流化::獲取類ID](#getclassid)|檢索物件的 CLSID。|
|[I 堅持流化::獲取 SizeMax](#getsizemax)|檢索保存對象數據所需的流的大小。 ATL 實現返回E_NOTIMPL。|
|[I 堅持流化::Initnew](#initnew)|初始化新創建的物件。|
|[我堅持流化::是肮髒的](#isdirty)|檢查物件的數據自上次保存以來是否已更改。|
|[I 堅持流化::載入](#load)|從指定的流載入物件的屬性。|
|[I 堅持流化::保存](#save)|將物件的屬性保存到指定的流。|

## <a name="remarks"></a>備註

[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面允許用戶端請求物件載入,並將其持久資料保存到單個流中。 類`IPersistStreamInitImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>I 堅持流化::獲取類ID

檢索物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱[IPersist:在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中獲取 ClassID。

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>I 堅持流化::獲取 SizeMax

檢索保存對象數據所需的流的大小。

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IPersistStreaminit:在](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax)Windows SDK 中獲取 SizeMax。

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>I 堅持流化::Initnew

初始化新創建的物件。

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>備註

請參閱[IPersistStreaminit::Windows](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) SDK 中的「新」。。

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>我堅持流化::是肮髒的

檢查物件的數據自上次保存以來是否已更改。

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>備註

請參閱[IPersistStreaminit:Windows](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) SDK 中髒話。

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>I 堅持流化::載入

從指定的流載入物件的屬性。

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射來檢索此資訊。

請參閱[IPersistStreaminit::](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load)在 Windows SDK 中載入。

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>I 堅持流化::保存

將物件的屬性保存到指定的流。

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>備註

ATL 使用物件的屬性映射來存儲此資訊。

請參閱[IPersistStreamInit::保存在](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[儲存和流](/windows/win32/Stg/storages-and-streams)<br/>
[類別概觀](../../atl/atl-class-overview.md)

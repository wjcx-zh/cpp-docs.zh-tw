---
title: IPersistStorageImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495697"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 類別

這個類別會實[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)介面。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IPersistStorageImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|抓取物件的 CLSID。|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示物件釋放所有儲存物件, 並進入 HandsOff 模式。 ATL 實作為傳回 S_OK。|
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的儲存體。|
|[IPersistStorageImpl::IsDirty](#isdirty)|檢查物件的資料自從上次儲存之後是否已變更。|
|[IPersistStorageImpl::Load](#load)|從指定的儲存體載入物件的屬性。|
|[IPersistStorageImpl::Save](#save)|將物件的屬性儲存至指定的儲存體。|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|通知物件, 它可以返回正常模式以寫入其儲存物件。 ATL 實作為傳回 S_OK。|

## <a name="remarks"></a>備註

`IPersistStorageImpl`會執行[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)介面, 這可讓用戶端要求您的物件載入, 並使用儲存體來儲存其持續性資料。

這個類別的執行需要類別`T` , 才能透過來`IPersistStreamInit`執行介面`QueryInterface`。 這通常表示類別`T`應該衍生自[ipersiststreaminitimpl<ccomspy>](../../atl/reference/ipersiststreaminitimpl-class.md), `IPersistStreamInit`在[COM 對應](com-map-macros.md)中提供的專案, 並使用[屬性對應](property-map-macros.md)來描述類別的持續性資料。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="getclassid"></a>IPersistStorageImpl::GetClassID

抓取物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) 。

##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

指示物件釋放所有儲存物件, 並進入 HandsOff 模式。

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) 。

##  <a name="initnew"></a>IPersistStorageImpl:: InitNew

初始化新的儲存體。

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>備註

ATL 的執行會委派給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。

請參閱 Windows SDK 中的[IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) 。

##  <a name="isdirty"></a>IPersistStorageImpl:: IsDirty

檢查物件的資料自從上次儲存之後是否已變更。

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>備註

ATL 的執行會委派給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。

請參閱 Windows SDK 中的[IPersistStorage: IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) 。

##  <a name="load"></a>IPersistStorageImpl:: Load

從指定的儲存體載入物件的屬性。

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>備註

ATL 的執行會委派給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 `Load`使用名為 "內容" 的資料流程來抓取物件的資料。 [Save](#save)方法原本會建立此資料流程。

請參閱[IPersistStorage:](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) Windows SDK 中的載入。

##  <a name="save"></a>IPersistStorageImpl:: Save

將物件的屬性儲存至指定的儲存體。

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>備註

ATL 的執行會委派給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 第`Save`一次呼叫時, 它會在指定的儲存體上建立名為 "內容" 的資料流程。 然後, 此資料流程會在稍後呼叫`Save`以[載入](#load)時使用。

請參閱[IPersistStorage:](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save)在 Windows SDK 中儲存。

##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

通知物件, 它可以返回正常模式以寫入其儲存物件。

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) 。

## <a name="see-also"></a>另請參閱

[儲存體和串流](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl 類別](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl 類別](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)

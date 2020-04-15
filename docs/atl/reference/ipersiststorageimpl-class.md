---
title: IPersist 儲存堆類
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
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326474"
---
# <a name="ipersiststorageimpl-class"></a>IPersist 儲存堆類

此類實現[IPersist 儲存](/windows/win32/api/objidl/nn-objidl-ipersiststorage)介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPersistStorageImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 檔案記憶體 impl:取得類別識別碼](#getclassid)|檢索物件的 CLSID。|
|[I 檔案記憶體 Impl::手關閉儲存](#handsoffstorage)|指示物件釋放所有存儲物件並進入"手關閉"模式。 ATL 實現返回S_OK。|
|[I 持久儲存 impl::ININnew](#initnew)|初始化新存儲。|
|[I 持久儲存 impl::是臟的](#isdirty)|檢查物件的數據自上次保存以來是否已更改。|
|[I 檔案記憶體 Impl::載入](#load)|從指定的存儲載入物件的屬性。|
|[IPersist 儲存impl::儲存](#save)|將物件的屬性保存到指定的存儲。|
|[IPersist 儲存impl::儲存完成](#savecompleted)|通知物件它可以返回到"正常"模式以寫入其存儲物件。 ATL 實現返回S_OK。|

## <a name="remarks"></a>備註

`IPersistStorageImpl`實現[IPersistStorage 介面](/windows/win32/api/objidl/nn-objidl-ipersiststorage),它允許用戶端請求物件載入並使用儲存保存其持久數據。

此類的實現要求類`T`通過`IPersistStreamInit`使介面的實現`QueryInterface`可用。 通常,`T`這意味著類應派生自[IPersistStreamInitImpl,](../../atl/reference/ipersiststreaminitimpl-class.md)在 COM`IPersistStreamInit`[映射](com-map-macros.md)中提供條目,並使用[屬性映射](property-map-macros.md)來描述類的持久數據。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>I 檔案記憶體 impl:取得類別識別碼

檢索物件的 CLSID。

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>備註

請參閱[IPersist:在](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid)Windows SDK 中獲取 ClassID。

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>I 檔案記憶體 Impl::手關閉儲存

指示物件釋放所有存儲物件並進入"手關閉"模式。

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IPersist 儲存::Windows SDK 中的「手關閉存儲](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage)」 。

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>I 持久儲存 impl::ININnew

初始化新存儲。

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>備註

ATL 實現委託給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。

請參閱[IPersist 儲存:Windows](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) SDK 中的 Init New。

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>I 持久儲存 impl::是臟的

檢查物件的數據自上次保存以來是否已更改。

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>備註

ATL 實現委託給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。

請參閱[IPersist 存儲:Windows](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) SDK 中髒汙。

## <a name="ipersiststorageimplload"></a><a name="load"></a>I 檔案記憶體 Impl::載入

從指定的存儲載入物件的屬性。

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>備註

ATL 實現委託給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 `Load`使用名為"內容"的流檢索物件的數據。 [Save](#save)方法最初創建此流。

請參閱[IPersist 存儲:在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load)Windows SDK 中載入。

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersist 儲存impl::儲存

將物件的屬性保存到指定的存儲。

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>備註

ATL 實現委託給[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)介面。 首次`Save`調用時,它會在指定的存儲上創建名為"內容"的流。 然後,此流用於以後對`Save` [Load](#load)的呼叫和呼叫 。

請參閱[IPersist 儲存:保存在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save)Windows SDK 中。

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersist 儲存impl::儲存完成

通知物件它可以返回到"正常"模式以寫入其存儲物件。

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IPersist 儲存:在](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted)Windows SDK 中保存已完成。

## <a name="see-also"></a>另請參閱

[儲存和流](/windows/win32/Stg/storages-and-streams)<br/>
[I 堅持流內普普類](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersist財產巴格普普類](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

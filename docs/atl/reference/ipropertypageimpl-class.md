---
title: IPropertyPageImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864979"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 類別

這個類別會實 `IUnknown` 並提供[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)介面的預設執行。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自 `IPropertyPageImpl`的類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPropertyPageImpl：： Activate](#activate)|建立屬性頁的對話方塊視窗。|
|[IPropertyPageImpl：： Apply](#apply)|將目前的屬性頁值套用至透過 `SetObjects`所指定的基礎物件。 ATL 執行會傳回 S_OK。|
|[IPropertyPageImpl：:D eactivate](#deactivate)|損毀使用 `Activate`建立的視窗。|
|[IPropertyPageImpl：： GetPageInfo](#getpageinfo)|抓取屬性頁的相關資訊。|
|[IPropertyPageImpl：： Help](#help)|叫用屬性頁的 Windows 說明。|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|指出屬性頁自啟動後是否已變更。|
|[IPropertyPageImpl：： Move](#move)|放置和調整屬性頁對話方塊的大小。|
|[IPropertyPageImpl::SetDirty](#setdirty)|將屬性頁的狀態標示為已變更或未變更。|
|[IPropertyPageImpl::SetObjects](#setobjects)|提供與屬性頁相關聯之物件的 `IUnknown` 指標陣列。 這些物件會透過呼叫 `Apply`來接收目前的屬性頁值。|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|提供具有 `IPropertyPageSite` 指標的屬性頁，屬性頁會透過它與屬性框架通訊。|
|[IPropertyPageImpl：： Show](#show)|使 [屬性頁] 對話方塊成為可見或隱藏。|
|[IPropertyPageImpl：： TranslateAccelerator](#translateaccelerator)|處理指定的按鍵。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IPropertyPageImpl：： m_bDirty](#m_bdirty)|指定屬性頁的狀態是否已變更。|
|[IPropertyPageImpl：： m_dwDocString](#m_dwdocstring)|儲存與描述屬性頁之文字字串相關聯的資源識別碼。|
|[IPropertyPageImpl：： m_dwHelpCoNtext](#m_dwhelpcontext)|儲存與屬性頁相關聯之說明主題的內容識別碼。|
|[IPropertyPageImpl：： m_dwHelpFile](#m_dwhelpfile)|儲存與描述屬性頁之說明檔名稱相關聯的資源識別碼。|
|[IPropertyPageImpl：： m_dwTitle](#m_dwtitle)|儲存與屬性頁的索引標籤中顯示之文字字串相關聯的資源識別碼。|
|[IPropertyPageImpl：： m_nObjects](#m_nobjects)|儲存與屬性頁相關聯的物件數目。|
|[IPropertyPageImpl：： m_pPageSite](#m_ppagesite)|指向屬性頁用來與屬性框架通訊的 `IPropertyPageSite` 介面。|
|[IPropertyPageImpl：： m_ppUnk](#m_ppunk)|指向與屬性頁相關聯之物件的 `IUnknown` 指標陣列。|
|[IPropertyPageImpl：： m_size](#m_size)|儲存屬性頁之對話方塊的高度和寬度（以圖元為單位）。|

## <a name="remarks"></a>備註

[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)介面可讓物件管理屬性工作表中的特定屬性頁。 類別 `IPropertyPageImpl` 會提供此介面的預設實值，並藉由將資訊傳送至偵錯工具中的傾印裝置來執行 `IUnknown`。

**相關文章** [atl 教學](../../atl/active-template-library-atl-tutorial.md)課程，[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl。h

##  <a name="activate"></a>IPropertyPageImpl：： Activate

建立屬性頁的對話方塊視窗。

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>備註

根據預設，不論*bModal*參數的值為何，對話方塊一律都是非模式。

請參閱 Windows SDK 中的[IPropertyPage：： Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) 。

##  <a name="apply"></a>IPropertyPageImpl：： Apply

將目前的屬性頁值套用至透過 `SetObjects`所指定的基礎物件。

```
HRESULT Apply();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) 。

##  <a name="deactivate"></a>IPropertyPageImpl：:D eactivate

終結以 [[啟動](#activate)] 建立的對話方塊視窗。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：:D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) 。

##  <a name="getpageinfo"></a>IPropertyPageImpl：： GetPageInfo

使用資料成員中包含的資訊填入*pPageInfo*結構。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>備註

`GetPageInfo` 會載入與[m_dwDocString](#m_dwdocstring)、 [m_dwHelpFile](#m_dwhelpfile)和[m_dwTitle](#m_dwtitle)相關聯的字串資源。

請參閱 Windows SDK 中的[IPropertyPage：： GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) 。

##  <a name="help"></a>IPropertyPageImpl：： Help

叫用屬性頁的 Windows 說明。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) 。

##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

建構函式。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>備註

初始化所有資料成員。

##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

指出屬性頁自啟動後是否已變更。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>備註

如果頁面自啟動後已變更，`IsPageDirty` 會傳回 S_OK。

##  <a name="m_bdirty"></a>IPropertyPageImpl：： m_bDirty

指定屬性頁的狀態是否已變更。

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl：： m_nObjects

儲存與屬性頁相關聯的物件數目。

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl：： m_dwHelpCoNtext

儲存與屬性頁相關聯之說明主題的內容識別碼。

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>IPropertyPageImpl：： m_dwDocString

儲存與描述屬性頁之文字字串相關聯的資源識別碼。

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl：： m_dwHelpFile

儲存與描述屬性頁之說明檔名稱相關聯的資源識別碼。

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl：： m_dwTitle

儲存與屬性頁的索引標籤中顯示之文字字串相關聯的資源識別碼。

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>IPropertyPageImpl：： m_pPageSite

指向[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)介面，屬性頁會透過它與屬性框架通訊。

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl：： m_ppUnk

指向與屬性頁相關聯之物件的 `IUnknown` 指標陣列。

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl：： m_size

儲存屬性頁之對話方塊的高度和寬度（以圖元為單位）。

```
SIZE m_size;
```

##  <a name="move"></a>IPropertyPageImpl：： Move

放置和調整屬性頁對話方塊的大小。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) 。

##  <a name="setdirty"></a>IPropertyPageImpl::SetDirty

視*bDirty*的值而定，將屬性頁的狀態標示為已變更或未變更。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>參數

*bDirty*<br/>
在若為 TRUE，則屬性頁的狀態會標示為已變更。 否則，它會標示為未變更。

### <a name="remarks"></a>備註

如有必要，`SetDirty` 通知框架屬性頁已變更。

##  <a name="setobjects"></a>IPropertyPageImpl::SetObjects

提供與屬性頁相關聯之物件的 `IUnknown` 指標陣列。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) 。

##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

提供具有[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)指標的屬性頁，屬性頁會透過它與屬性框架通訊。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) 。

##  <a name="show"></a>IPropertyPageImpl：： Show

使 [屬性頁] 對話方塊成為可見或隱藏。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) 。

##  <a name="translateaccelerator"></a>IPropertyPageImpl：： TranslateAccelerator

處理 `pMsg`中指定的按鍵。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IPropertyPage：： TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) 。

## <a name="see-also"></a>另請參閱

[IPropertyPage2Impl 類別](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)

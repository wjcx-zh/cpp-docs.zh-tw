---
title: IPropertypageimpl 類別
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
ms.openlocfilehash: ac8fcb3b8b2bd0f876cf28d58e195000112373f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329580"
---
# <a name="ipropertypageimpl-class"></a>IPropertypageimpl 類別

此類實現`IUnknown`並提供[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)介面的預設實現。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IPropertyPageImpl`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[I屬性頁頁::I屬性頁頁](#ipropertypageimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IPropertyPageimpl::啟動](#activate)|為屬性頁創建對話框視窗。|
|[IPropertypage:應用](#apply)|將當前屬性頁值應用於通過`SetObjects`指定的基礎物件。 ATL 實現返回S_OK。|
|[IPropertyPageimpl::D啟動](#deactivate)|銷毀使用`Activate`創建的視窗。|
|[IPropertyPageimpl::取得Pageinfo](#getpageinfo)|檢索有關屬性頁的資訊。|
|[IPropertyPageimpl::説明](#help)|調用屬性頁的 Windows 説明。|
|[I屬性頁頁::是頁面臟](#ispagedirty)|指示屬性頁自啟動以來是否已更改。|
|[I 屬性頁頁:移動](#move)|定位屬性頁對話框並調整大小。|
|[I屬性頁頁::設定髒](#setdirty)|將屬性頁的狀態標記為已更改或未更改。|
|[IPropertypageimpl::設定物件](#setobjects)|為與屬性頁`IUnknown`關聯的物件提供指標陣列。 這些物件通過調用`Apply`接收當前屬性頁值。|
|[I 屬性頁頁::設定頁面網站](#setpagesite)|使用`IPropertyPageSite`指標向屬性頁提供,屬性頁通過該指標與屬性框架通信。|
|[IPropertyPageimpl::顯示](#show)|使屬性頁對話框可見或不可見。|
|[IPropertyPageimpl::翻譯加速器](#translateaccelerator)|處理指定的擊鍵。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IPropertyPageimpl::m_bDirty](#m_bdirty)|指定屬性頁的狀態是否已更改。|
|[IPropertyPageimpl::m_dwDocString](#m_dwdocstring)|儲存與描述屬性頁的文字字串關聯的資源標識碼。|
|[IPropertyPageimpl::m_dwHelpContext](#m_dwhelpcontext)|儲存與屬性頁關聯的幫助主題的上下文標識碼。|
|[IPropertyPageimpl:m_dwHelpFile](#m_dwhelpfile)|儲存與描述屬性頁的説明檔的名稱關聯的資源標識碼。|
|[IPropertyPageimpl::m_dwTitle](#m_dwtitle)|儲存與顯示在屬性頁的選項卡中的文字字串關聯的資源標識符。|
|[IPropertyPageimpl::m_nObjects](#m_nobjects)|存儲與屬性頁關聯的物件數。|
|[IPropertyPageimpl::m_pPageSite](#m_ppagesite)|指向屬性頁`IPropertyPageSite`通過該介面與屬性框架通信的介面。|
|[IPropertypage:m_ppUnk](#m_ppunk)|指向指向與屬性頁`IUnknown`關聯的物件的指標陣列。|
|[IPropertyPageimpl::m_size](#m_size)|存儲屬性頁對話方塊的高度和寬度(以像素為單位)。|

## <a name="remarks"></a>備註

[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)介面允許物件管理屬性表中的特定屬性頁。 類`IPropertyPageImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageimpl::啟動

為屬性頁創建對話框視窗。

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>備註

默認情況下,無論*bModal*參數的值如何,對話框始終處於無模式狀態。

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate)Windows SDK 中啟動。

## <a name="ipropertypageimplapply"></a><a name="apply"></a>IPropertypage:應用

將當前屬性頁值應用於通過`SetObjects`指定的基礎物件。

```
HRESULT Apply();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IPropertyPage::在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply)Windows SDK 中應用。

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageimpl::D啟動

銷毀使用[啟動](#activate)創建的對話框視窗。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage::D在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate)Windows SDK 中啟動。

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageimpl::取得Pageinfo

使用數據成員中包含的資訊填充*pPageInfo*結構。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>備註

`GetPageInfo`載入與[m_dwDocString、m_dwHelpFile](#m_dwdocstring)和[m_dwHelpFile](#m_dwhelpfile)[m_dwTitle](#m_dwtitle)關聯的 字串資源。

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo)Windows SDK 中獲取Pageinfo。

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageimpl::説明

調用屬性頁的 Windows 説明。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:Windows](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) SDK 中的説明。

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>I屬性頁頁::I屬性頁頁

建構函式。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>備註

初始化所有數據成員。

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>I屬性頁頁::是頁面臟

指示屬性頁自啟動以來是否已更改。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>備註

`IsPageDirty`如果頁面自啟動以來已更改,則返回S_OK。

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageimpl::m_bDirty

指定屬性頁的狀態是否已更改。

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageimpl::m_nObjects

存儲與屬性頁關聯的物件數。

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageimpl::m_dwHelpContext

儲存與屬性頁關聯的幫助主題的上下文標識碼。

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageimpl::m_dwDocString

儲存與描述屬性頁的文字字串關聯的資源標識碼。

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageimpl:m_dwHelpFile

儲存與描述屬性頁的説明檔的名稱關聯的資源標識碼。

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageimpl::m_dwTitle

儲存與顯示在屬性頁的選項卡中的文字字串關聯的資源標識符。

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageimpl::m_pPageSite

指向[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)介面,屬性頁通過該介面與屬性框架通信。

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertypage:m_ppUnk

指向指向與屬性頁`IUnknown`關聯的物件的指標陣列。

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageimpl::m_size

存儲屬性頁對話方塊的高度和寬度(以像素為單位)。

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>I 屬性頁頁:移動

定位屬性頁對話框並調整大小。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move)Windows SDK 中移動。

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>I屬性頁頁::設定髒

根據*bDirty*的值,將屬性頁的狀態標記為已更改或未更改。

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>參數

*bDirty*<br/>
[在]如果為 TRUE,則屬性頁的狀態將標記為已更改。 否則,它將標記為未更改。

### <a name="remarks"></a>備註

如有必要,`SetDirty`通知框架屬性頁已更改。

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>IPropertypageimpl::設定物件

為與屬性頁`IUnknown`關聯的物件提供指標陣列。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects)Windows SDK 中設置物件。

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>I 屬性頁頁::設定頁面網站

使用[IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite)指標提供屬性頁,屬性頁透過該指標與屬性框架通信。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite)Windows SDK 中設置PageSite。

## <a name="ipropertypageimplshow"></a><a name="show"></a>IPropertyPageimpl::顯示

使屬性頁對話框可見或不可見。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show)Windows SDK 中顯示。

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageimpl::翻譯加速器

處理`pMsg`中 指定的擊鍵。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>備註

請參閱[IPropertyPage:在](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator)Windows SDK 中翻譯加速器。

## <a name="see-also"></a>另請參閱

[IPropertypage2Impl 類](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerProperty 瀏覽類別](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[I 指定屬性頁頁類別](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)

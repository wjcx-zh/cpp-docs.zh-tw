---
title: IPropertyPageImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f86b93bad181fdbac5763bd215b0ec28ab50296
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365350"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 類別
這個類別會實作**IUnknown**和提供的預設實作[IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPropertyPageImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|建立屬性頁對話方塊視窗。|  
|[IPropertyPageImpl::Apply](#apply)|目前屬性頁的值會套用至基礎物件透過指定`SetObjects`。 ATL 實作會傳回`S_OK`。|  
|[IPropertyPageImpl::Deactivate](#deactivate)|終結視窗以建立**Activate**。|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|擷取屬性頁的相關資訊。|  
|[IPropertyPageImpl::Help](#help)|叫用屬性頁的 Windows 的說明。|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|表示屬性頁是否已變更，因為它已啟動。|  
|[IPropertyPageImpl::Move](#move)|放置並調整大小屬性頁對話方塊。|  
|[IPropertyPageImpl::SetDirty](#setdirty)|旗標已變更或未變更的屬性頁的狀態。|  
|[IPropertyPageImpl::SetObjects](#setobjects)|提供的陣列**IUnknown**屬性頁相關聯物件的指標。 這些物件會接收目前的屬性頁面值，透過呼叫**套用**。|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|提供的屬性頁面`IPropertyPageSite`指標，透過此屬性頁與屬性框架的通訊。|  
|[IPropertyPageImpl::Show](#show)|可見或不可見，可讓 [屬性頁] 對話方塊。|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|處理指定的按鍵。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|指定是否已變更屬性頁的狀態。|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|儲存文字字串描述屬性頁相關聯的資源識別碼。|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|會儲存相關聯的屬性頁的 [說明] 主題的內容識別項。|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|儲存與描述 屬性頁的說明檔的名稱相關聯的資源識別碼。|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|儲存出現在屬性頁 索引標籤的文字字串相關聯的資源識別碼。|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|儲存屬性頁相關聯的物件數目。|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|指向`IPropertyPageSite`透過此屬性頁會與屬性框架通訊的介面。|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|指向陣列**IUnknown**屬性頁相關聯的物件的指標。|  
|[IPropertyPageImpl::m_size](#m_size)|像素為單位儲存的高度和寬度屬性頁 對話方塊。|  
  
## <a name="remarks"></a>備註  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246)介面，允許物件來管理特定的屬性頁中的屬性工作表。 類別`IPropertyPageImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="activate"></a>  IPropertyPageImpl::Activate  
 建立屬性頁對話方塊視窗。  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>備註  
 根據預設，對話方塊會非強制回應的值為何*bModal*參數。  
  
 請參閱[IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) Windows SDK 中。  
  
##  <a name="apply"></a>  IPropertyPageImpl::Apply  
 目前屬性頁的值會套用至基礎物件透過指定`SetObjects`。  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) Windows SDK 中。  
  
##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate  
 終結對話方塊視窗建立具有[Activate](#activate)。  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) Windows SDK 中。  
  
##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo  
 填滿*pPageInfo*結構與資料成員中包含的資訊。  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>備註  
 `GetPageInfo` 載入與相關聯的字串資源[m_dwDocString](#m_dwdocstring)， [m_dwHelpFile](#m_dwhelpfile)，和[m_dwTitle](#m_dwtitle)。  
  
 請參閱[IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) Windows SDK 中。  
  
##  <a name="help"></a>  IPropertyPageImpl::Help  
 叫用屬性頁的 Windows 的說明。  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) Windows SDK 中。  
  
##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl  
 建構函式。  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>備註  
 初始化所有的資料成員。  
  
##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty  
 表示屬性頁是否已變更，因為它已啟動。  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>備註  
 `IsPageDirty` 傳回`S_OK`如果頁面已經變更，因為它已啟動。  
  
##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty  
 指定是否已變更屬性頁的狀態。  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects  
 儲存屬性頁相關聯的物件數目。  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext  
 會儲存相關聯的屬性頁的 [說明] 主題的內容識別項。  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString  
 儲存文字字串描述屬性頁相關聯的資源識別碼。  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile  
 儲存與描述 屬性頁的說明檔的名稱相關聯的資源識別碼。  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle  
 儲存出現在屬性頁 索引標籤的文字字串相關聯的資源識別碼。  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite  
 指向[IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583)透過此屬性頁會與屬性框架通訊的介面。  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk  
 指向陣列**IUnknown**屬性頁相關聯的物件的指標。  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>  IPropertyPageImpl::m_size  
 像素為單位儲存的高度和寬度屬性頁 對話方塊。  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>  IPropertyPageImpl::Move  
 放置並調整大小屬性頁對話方塊。  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) Windows SDK 中。  
  
##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty  
 屬性頁的狀態為已變更或不變，根據的值加上旗標`bDirty`。  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>參數  
 `bDirty`  
 [in]如果**TRUE**，屬性頁的狀態會標記為已變更。 否則，它會標示為不變。  
  
### <a name="remarks"></a>備註  
 如有必要，`SetDirty`通知已變更屬性頁的框架。  
  
##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects  
 提供的陣列**IUnknown**屬性頁相關聯物件的指標。  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) Windows SDK 中。  
  
##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite  
 提供的屬性頁面[IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583)指標，透過此屬性頁與屬性框架的通訊。  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) Windows SDK 中。  
  
##  <a name="show"></a>  IPropertyPageImpl::Show  
 可見或不可見，可讓 [屬性頁] 對話方塊。  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) Windows SDK 中。  
  
##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator  
 處理中指定的按鍵動作`pMsg`。  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [IPropertyPage2Impl 類別](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl 類別](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl 類別](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

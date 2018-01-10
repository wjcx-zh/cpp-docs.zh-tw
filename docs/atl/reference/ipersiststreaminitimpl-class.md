---
title: "IPersistStreamInitImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs: C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fe1bcd8d8198304c92584f01522048c4d29b827
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl 類別
這個類別會實作**IUnknown**和提供的預設實作[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPersistStreamInitImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|擷取物件的 CLSID。|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|擷取儲存物件的資料所需的資料流的大小。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IPersistStreamInitImpl::InitNew](#initnew)|初始化新建立的物件。|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|檢查自上次儲存後，是否已變更物件的資料。|  
|[IPersistStreamInitImpl::Load](#load)|從指定的資料流載入物件的屬性。|  
|[IPersistStreamInitImpl::Save](#save)|將物件的屬性儲存至指定的資料流。|  
  
## <a name="remarks"></a>備註  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)介面可讓用戶端要求載入您的物件，並將其永續性資料儲存至單一資料流。 類別`IPersistStreamInitImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStreamInitImpl::GetClassID  
 擷取物件的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>備註  
 請參閱[ipersist:: Getclassid](http://msdn.microsoft.com/library/windows/desktop/ms688664) Windows SDK 中。  
  
##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax  
 擷取儲存物件的資料所需的資料流的大小。  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) Windows SDK 中。  
  
##  <a name="initnew"></a>IPersistStreamInitImpl::InitNew  
 初始化新建立的物件。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) Windows SDK 中。  
  
##  <a name="isdirty"></a>IPersistStreamInitImpl::IsDirty  
 檢查自上次儲存後，是否已變更物件的資料。  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) Windows SDK 中。  
  
##  <a name="load"></a>IPersistStreamInitImpl::Load  
 從指定的資料流載入物件的屬性。  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>備註  
 ATL 會使用物件的屬性對應，來擷取這項資訊。  
  
 請參閱[IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) Windows SDK 中。  
  
##  <a name="save"></a>IPersistStreamInitImpl::Save  
 將物件的屬性儲存至指定的資料流。  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>備註  
 ATL 會使用物件的屬性對應儲存這項資訊。  
  
 請參閱[IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [儲存體和資料流](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [類別概觀](../../atl/atl-class-overview.md)

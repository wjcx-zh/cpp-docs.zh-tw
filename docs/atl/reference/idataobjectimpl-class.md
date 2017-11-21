---
title: "IDataObjectImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
dev_langs: C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be2fbd11ac875906c9fc4fca4c58d3979f49cc3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl 類別
這個類別會提供方法以支援制式資料傳輸，並管理連接。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IDataObjectImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|建立資料物件和通知接收之間的連接。 這可讓通知接收以接收的變更通知的物件。|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|終止透過先前建立的連線`DAdvise`。|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|建立來逐一查看目前諮詢連接的列舉值。|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|建立來逐一查看的列舉值**FORMATETC**資料物件支援的結構。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|將變更通知傳回給每一個通知接收。|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|擷取邏輯對等**FORMATETC**為更複雜的結構。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IDataObjectImpl::GetData](#getdata)|將資料從資料物件傳輸到用戶端。 說明資料**FORMATETC**結構，並透過傳送**STGMEDIUM**結構。|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|類似於`GetData`，除了用戶端必須配置**STGMEDIUM**結構。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|決定資料的物件是否支援特定**FORMATETC**傳送資料的結構。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IDataObjectImpl::SetData](#setdata)|將資料從用戶端傳輸至資料物件。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)介面提供方法來支援制式資料傳輸。 `IDataObject`使用標準格式結構[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)和[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)來擷取及儲存資料。  
  
 `IDataObject`也會管理連線到通知接收來處理資料變更通知。 為了讓用戶端收到的資料物件的資料變更通知，在用戶端必須實作[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)呼叫通知接收物件上的介面。 當用戶端再呼叫**IDataObject::DAdvise**，資料物件和通知接收之間建立連線。  
  
 類別`IDataObjectImpl`提供的預設實作`IDataObject`並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="dadvise"></a>IDataObjectImpl::DAdvise  
 建立資料物件和通知接收之間的連接。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>備註  
 這可讓通知接收以接收的變更通知的物件。  
  
 若要終止的連接，呼叫[DUnadvise](#dunadvise)。  
  
 請參閱[IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) Windows SDK 中。  
  
##  <a name="dunadvise"></a>IDataObjectImpl::DUnadvise  
 終止透過先前建立的連線[DAdvise](#dadvise)。  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) Windows SDK 中。  
  
##  <a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise  
 建立來逐一查看目前諮詢連接的列舉值。  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) Windows SDK 中。  
  
##  <a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc  
 建立來逐一查看的列舉值**FORMATETC**資料物件支援的結構。  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
##  <a name="firedatachange"></a>IDataObjectImpl::FireDataChange  
 將變更通知傳回給目前受管理的每個通知接收。  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc  
 擷取邏輯對等**FORMATETC**為更複雜的結構。  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) Windows SDK 中。  
  
##  <a name="getdata"></a>IDataObjectImpl::GetData  
 將資料從資料物件傳輸到用戶端。  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>備註  
 *PformatetcIn*參數必須指定的儲存媒體類型**TYMED_MFPICT**。  
  
 請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="getdatahere"></a>IDataObjectImpl::GetDataHere  
 類似於`GetData`，除了用戶端必須配置**STGMEDIUM**結構。  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::GetDataHere](http://msdn.microsoft.com/library/windows/desktop/ms687266) Windows SDK 中。  
  
##  <a name="querygetdata"></a>IDataObjectImpl::QueryGetData  
 決定資料的物件是否支援特定**FORMATETC**傳送資料的結構。  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) Windows SDK 中。  
  
##  <a name="setdata"></a>IDataObjectImpl::SetData  
 將資料從用戶端傳輸至資料物件。  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IDataObject::SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

---
title: IRowsetNotifyImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a20be1a92c93be38d901f58339bb02b24cf2661f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339951"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl 類別
實作並註冊[IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx)上取用者 （也稱為 「 接收 」），使其可以處理通知。  
  
## <a name="syntax"></a>語法

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  

## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[OnFieldChange](#onfieldchange)|告知消費者的資料行值的任何變更。|  
|[OnRowChange](#onrowchange)|告知消費者，資料列的第一個變更或影響整個資料列的任何變更。|  
|[OnRowsetChange](#onrowsetchange)|通知任何變更會影響整個資料列集取用的者。|  
  
## <a name="remarks"></a>備註  
 請參閱[接收通知](../../data/oledb/receiving-notifications.md)需於取用者實作連接點介面。  
  
 `IRowsetNotifyImpl` 提供的虛擬實作`IRowsetNotify`，使用空白的函式`IRowsetNotify`方法[OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx)， [OnRowChange](https://msdn.microsoft.com/library/ms722694.aspx)，和[OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx). 如果您繼承自這個類別實作時`IRowsetNotify`介面，您可以實作只有您所需的方法。 您也需要自行提供空的實作，如需其他方法。  

## <a name="onfieldchange"></a> Irowsetnotifyimpl:: Onfieldchange
告知消費者的資料行值的任何變更。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx)的參數說明。  
  
### <a name="return-value"></a>傳回值  
 請參閱[IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx)的回傳值描述。  
  
### <a name="remarks"></a>備註  
 這個方法會包裝[IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/library/ms715961.aspx)方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。  

## <a name="onrowchange"></a> Irowsetnotifyimpl:: Onrowchange
告知消費者，資料列的第一個變更或影響整個資料列的任何變更。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/library/ms722694.aspx)的參數說明。  
  
### <a name="return-value"></a>傳回值  
 請參閱[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/library/ms722694.aspx)的回傳值描述。  
  
### <a name="remarks"></a>備註  
 這個方法會包裝[irowsetnotify:: Onrowchange](https://msdn.microsoft.com/library/ms722694.aspx)方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。 

## <a name="onrowsetchange"></a> Irowsetnotifyimpl:: Onrowsetchange
通知任何變更會影響整個資料列集取用的者。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx)的參數說明。  
  
### <a name="return-value"></a>傳回值  
 請參閱[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx)的回傳值描述。  
  
### <a name="remarks"></a>備註  
 這個方法會包裝[IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/library/ms722669.aspx)方法。 請參閱《OLE DB 程式設計人員參考》中該方法的說明以取得詳細資訊。
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx)   
 [IRowsetNotifyCP 類別](../../data/oledb/irowsetnotifycp-class.md)
---
title: "IRowsetNotifyCP 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IRowsetNotifyCP
dev_langs: C++
helpviewer_keywords: IRowsetNotifyCP class
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d110b3bc304664681532ae7511a9e886a05058b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP 類別
實作連接點介面的提供者站台[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   class T,   
   class ReentrantEventSync = CComSharedMutex   
>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray  
   >,  
   public ReentrantEventSync  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IRowsetNotifyCP`。  
  
 `ReentrantEventSync`  
 支援重新進入的 mutex 類別 (預設值是**CComSharedMutex**)。 Mutex 是允許執行緒互斥存取資源的同步處理物件。  
  
 `piid`  
 介面識別碼指標 (**IID\***) 的**IRowsetNotify**連接點介面。 預設值是**& __uuidof(IRowsetNotify)**。  
  
 `DynamicUnkArray`  
 類型的陣列[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，即為動態配置的陣列**IUnknown**指標給用戶端接收的介面。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[Fire_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|通知變更的資料行值的取用者。|  
|[Fire_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|通知變更會影響資料列的取用者。|  
|[Fire_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|通知變更會影響整個資料列集取用的者。|  
  
## <a name="remarks"></a>備註  
 `IRowsetNotifyCP`實作廣播函式來通知接聽程式連接點上**IID_IRowsetNotify**的資料列集內容的變更。  
  
 請注意，您也必須實作並註冊`IRowsetNotify`上取用者 （也稱為 「 接收 」） 使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，好讓取用者可以處理通知。 請參閱[接收通知](../../data/oledb/receiving-notifications.md)有關上取用者實作連接點介面。  
  
 實作通知的詳細資訊，請參閱 [支援的通知]，在[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [通知 (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)
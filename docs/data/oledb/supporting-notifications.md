---
title: "支援告知 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a859a9f3b2061d1cb18c93cd9f46d30600ada28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-notifications"></a>支援告知
## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>上的提供者和取用者實作連接點介面  
 若要實作通知，提供者類別必須繼承自[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)和[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。  
  
 `IRowsetNotifyCP`實作連接點介面的提供者站台[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)。 `IRowsetNotifyCP`實作廣播函式來通知接聽程式連接點上**IID_IRowsetNotify**的資料列集內容的變更。  
  
 請注意，您也必須實作並註冊`IRowsetNotify`上取用者 （也稱為接收） 使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，好讓取用者可以處理通知。 在取用者實作連接點介面的詳細資訊，請參閱[接收通知](../../data/oledb/receiving-notifications.md)。  
  
 此外，類別也必須包含的地圖，定義的連接點項目，就像這樣：  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>加入 IRowsetNotify  
 若要加入`IRowsetNotify`，您需要加入`IConnectionPointContainerImpl<rowset-name>`和`IRowsetNotifyCP<rowset-name>`繼承鏈結。  
  
 例如，以下是的繼承鏈結`RUpdateRowset`中[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  從此處; 所列的範例程式碼可能會與不同您應該將範例程式碼視為最新的版本。  
  
```  
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan> >, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll > >,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>設定 COM 對應項目  
 您還需要 COM 中的對應資料列集加上下列：  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 這些巨集可以讓任何人呼叫`QueryInterface`連接點容器 (的基礎`IRowsetNotify`) 來尋找您的提供者上要求的介面。 如需如何使用連線點的範例，請參閱 ATL 多邊形範例與教學課程。  
  
### <a name="setting-connection-point-map-entries"></a>設定連線點對應項目  
 您也需要加入連接點對應。 它看起來應該像這樣：  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 此連接點對應可讓元件尋找`IRowsetNotify`介面，以在您的提供者中找到它。  
  
### <a name="setting-properties"></a>設定屬性  
 您也需要將下列屬性加入至您的提供者。 您只需要加入您所支援的介面為基礎的屬性。  
  
|屬性|支援時應加入|  
|--------------|------------------------|  
|**DBPROP_IConnectionPointContainer**|永遠|  
|**DBPROP_NOTIFICATIONGRANULARITY**|永遠|  
|**DBPROP_NOTIFICATIONPHASES**|永遠|  
|**DBPROP_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE**|永遠|  
|**DBPROP_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWSETRELEASE**|永遠|  
|**DBPROP_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 大部分的通知的實作已內嵌於 OLE DB 提供者樣板。 如果您需要新增`IRowsetNotifyCP`至您的繼承鏈結，編譯器會移除所有的程式碼編譯資料流，而讓程式碼大小較小。  
  
## <a name="see-also"></a>請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
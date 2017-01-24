---
title: "支援告知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件 [C++], OLE DB 中的告知"
  - "告知 [C++], OLE DB 消費者"
  - "OLE DB 消費者, 告知"
  - "OLE DB 提供者樣板, 告知"
  - "OLE DB 提供者, 告知"
  - "資料列集, 事件告知"
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支援告知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 實作提供者和消費者的連接點介面  
 若要實作告知，提供者 \(Provider\) 類別必須繼承自 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) 和 [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。  
  
 `IRowsetNotifyCP` 實作連接點介面 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 的提供者網站。  `IRowsetNotifyCP` 則實作廣播功能，以通知在 **IID\_IRowsetNotify** 連接點上的接聽程式關於資料列集內容的變更。  
  
 請注意，您也必須使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 來實作並登錄在消費者上的 `IRowsetNotify` \(亦稱為接收\)，以便讓消費者可處理告知。  如需在消費者上實作連接點介面的詳細資訊，請參閱[接收告知](../../data/oledb/receiving-notifications.md)。  
  
 此外，類別也必須包含定義連接點 \(Connection Point\) 項目的對應，例如：  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## 加入 IRowsetNotify  
 若要加入 `IRowsetNotify`，您需要將 `IConnectionPointContainerImpl<rowset-name>` 和 `IRowsetNotifyCP<rowset-name>` 加入至繼承鏈結。  
  
 例如，以下為 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 內的 `RUpdateRowset` 繼承鏈結：  
  
> [!NOTE]
>  範例程式碼可能會與此處所列的有所不同，您應該視範例程式碼為最新的版本。  
  
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
  
### 設定 COM 對應項目  
 您還需要將下列程式碼加入至資料列集的 COM 對應：  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 這些巨集可讓任何人呼叫連接點容器 \(Container\) 的 `QueryInterface` \(`IRowsetNotify` 的基礎\)，以便在提供者內尋找要求的介面。  如需如何使用連結點的範例，請參閱 ATL POLYGON 範例和教學課程。  
  
### 設定連接點對應項目  
 您也需要加入連接點對應。  程式碼類似以下內容：  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 這個連接點對應會讓搜尋 `IRowsetNotify` 介面的元件在提供者內尋找連接點對應。  
  
### 設定屬性  
 您也需要將下列屬性加入提供者 \(Provider\) 內。  您只需要根據支援的介面加入屬性。  
  
|屬性|支援時應加入|  
|--------|------------|  
|**DBPROP\_IConnectionPointContainer**|永遠|  
|**DBPROP\_NOTIFICATIONGRANULARITY**|永遠|  
|**DBPROP\_NOTIFICATIONPHASES**|永遠|  
|**DBPROP\_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWSETFETCHPOSITIONCHANGE**|永遠|  
|**DBPROP\_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWSETRELEASE**|永遠|  
|**DBPROP\_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 多數告知的實作都已內嵌至 OLE DB 提供者樣板內。  由於 Visual C\+\+ .NET 的編譯器 \(Compiler\) 特性，如果您未將 `IRowsetNotifyCP` 加入至繼承鏈結內，編譯器會從編譯資料流中移除所有程式碼，以便縮小程式碼大小。  
  
## 請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
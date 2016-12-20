---
title: "CMyProviderCommand (MyProviderRS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyprovidercommand"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderRS.H 中的 CMyProviderCommand 類別"
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderCommand (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMyProviderCommand` 類別是提供者命令物件的實作。  此類別提供 `IAccessor`、`ICommandText` 和 **ICommandProperties** 介面的實作。  `IAccessor` 介面和資料列集 \(Rowset\) 內的介面相同。  命令物件會使用存取子 \(Accessor\) 來指定參數的繫結。  資料列集物件會使用這些存取子來指定輸出資料行的繫結。  `ICommandText` 介面是以文字指定命令的有用方式。  此範例稍後在加入自訂程式碼時，會使用 `ICommandText` 介面，它也會覆寫 `ICommand::Execute` 方法。  **ICommandProperties** 介面可處理命令和資料列集物件的所有屬性。  
  
```  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 `IAccessor` 介面可管理命令和資料列集所使用的所有繫結。  消費者會以 **DBBINDING** 結構的陣列來呼叫 **IAccessor::CreateAccessor**。  每個 **DBBINDING** 結構都包含應該如何處理資料行繫結的資訊 \(例如型別和長度\)。  提供者接收結構，然後決定資料應如何傳送，以及是否需做任何轉換。  `IAccessor` 介面將用於命令物件中，以處理命令內的任何參數。  
  
 命令物件也提供 `IColumnsInfo` 的實作。  OLE DB 需要 `IColumnsInfo` 介面。  此介面可讓消費者從命令擷取參數的相關資訊。  資料列集物件使用 `IColumnsInfo` 介面將輸出資料行的相關資訊傳回給提供者。  
  
 提供者也包含了一個名為 `IObjectWithSite` 的介面。  `IObjectWithSite` 介面是以 ATL 2.0 來實作，並允許實作器將它本身的資訊傳給其子系。  命令物件使用 `IObjectWithSite` 資訊來讓任何產生的資料列集物件知道是誰建立它們。  
  
## 請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
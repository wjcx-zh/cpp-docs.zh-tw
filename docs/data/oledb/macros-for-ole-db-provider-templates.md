---
title: "OLE DB 提供者樣板的巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "巨集, OLE DB 提供者樣板"
  - "OLE DB 提供者樣板巨集"
  - "OLE DB 提供者樣板, 巨集"
  - "提供者樣板巨集 (OLE DB)"
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE DB 提供者樣板的巨集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 提供者樣板巨集提供下列分類的功能:  
  
### 屬性集對應  
  
|||  
|-|-|  
|[BEGIN\_PROPERTY\_SET](../../data/oledb/begin-property-set.md)|標記屬性集合的開頭。|  
|[BEGIN\_PROPERTY\_SET\_EX](../../data/oledb/begin-property-set-ex.md)|標記屬性集合的開頭。|  
|[BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)|標記必須在提供者範圍之外，可以隱藏或定義設定的屬性的開頭。|  
|[CHAIN\_PROPERTY\_SET](../../data/oledb/chain-property-set.md)|鏈結屬性群組。|  
|[END\_PROPERTY\_SET](../../data/oledb/end-property-set.md)|標記屬性集合的結尾。|  
|[END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md)|標記屬性地圖的結尾。|  
|[PROPERTY\_INFO\_ENTRY](../../data/oledb/property-info-entry.md)|在屬性上設定特定屬性設定為預設值。|  
|[PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md)|在屬性上設定特定屬性設定為您提供的值。  此外也可讓您設定旗標和選項。|  
|[PROPERTY\_INFO\_ENTRY\_VALUE](../../data/oledb/property-info-entry-value.md)|在屬性上設定特定屬性設定為您提供的值。|  
  
### 資料行對應巨集  
  
|||  
|-|-|  
|[BEGIN\_PROVIDER\_COLUMN\_MAP](../../data/oledb/begin-provider-column-map.md)|標籤提供者資料行對應項目的開頭。|  
|[END\_PROVIDER\_COLUMN\_MAP](../../data/oledb/end-provider-column-map.md)|標記提供者對應項目的結尾。|  
|[PROVIDER\_COLUMN\_ENTRY](../../data/oledb/provider-column-entry.md)|表示提供者支援的特定資料行。|  
|[PROVIDER\_COLUMN\_ENTRY\_GN](../../data/oledb/provider-column-entry-gn.md)|表示提供者支援的特定資料行。  您可以指定資料行的大小、資料型別、精確度、小數點位數和結構描述資料列集 GUID。|  
|[PROVIDER\_COLUMN\_ENTRY\_FIXED](../../data/oledb/provider-column-entry-fixed.md)|表示提供者支援的特定資料行。  您可以指定資料行的資料型別。|  
|[PROVIDER\_COLUMN\_ENTRY\_LENGTH](../../data/oledb/provider-column-entry-length.md)|表示提供者支援的特定資料行。  您可以指定資料行的大小。|  
|[PROVIDER\_COLUMN\_ENTRY\_STR](../../data/oledb/provider-column-entry-str.md)|表示提供者支援的特定資料行。  它假設資料行型別是字串。|  
|[PROVIDER\_COLUMN\_ENTRY\_TYPE\_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|表示提供者支援的特定資料行。  與 PROVIDER\_COLUMN\_ENTRY\_LENGTH 類似，但是可讓您指定資料行的資料型別和大小。|  
|[PROVIDER\_COLUMN\_ENTRY\_WSTR](../../data/oledb/provider-column-entry-wstr.md)|表示提供者支援的特定資料行。  它假設資料行是 Unicode 字串。|  
  
### 結構描述資料列集巨集  
  
|||  
|-|-|  
|[BEGIN\_SCHEMA\_MAP](../../data/oledb/begin-schema-map.md)|標記結構描述對應的開頭。|  
|[SCHEMA\_ENTRY](../../data/oledb/schema-entry.md)|將GUID與類別的產生關聯。|  
|[END\_SCHEMA\_MAP](../../data/oledb/end-schema-map.md)|標記結構描述對應的結尾。|  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 提供者樣板參考](../../data/oledb/ole-db-provider-templates-reference.md)
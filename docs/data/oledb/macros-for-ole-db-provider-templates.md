---
title: "OLE DB 提供者樣板的巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.templates.ole
dev_langs: C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a61e8156b39b9f0afec477f541920570d4af823
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="macros-for-ole-db-provider-templates"></a>OLE DB 提供者樣板的巨集
OLE DB 樣板提供者巨集提供下列分類中的功能：  
  
### <a name="property-set-map-macros"></a>屬性會設定對應巨集  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|標記的屬性集的開頭。|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|標記的屬性集的開頭。|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|屬性的開頭設定的標記可以隱藏或定義範圍以外的提供者。|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|鏈結在一起，屬性群組。|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|標示屬性集的結尾。|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|結束標記的屬性集對應。|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|設定特定的屬性中將屬性設定為預設值。|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|設定特定的屬性中將屬性設定為您所提供的值。 也可讓您設定旗標和選項。|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|設定特定的屬性中將屬性設定為您所提供的值。|  
  
### <a name="column-map-macros"></a>資料行對應巨集  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|標記提供者的資料行對應項目的開頭。|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|提供者的資料行對應項目結束標記。|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|表示提供者支援的特定資料行。|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|表示提供者支援的特定資料行。 您可以指定資料行的大小、 資料類型、 有效位數、 小數位數和結構描述資料列集 GUID。|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|表示提供者支援的特定資料行。 您可以指定資料行資料類型。|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|表示提供者支援的特定資料行。 您可以指定資料行大小。|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|表示提供者支援的特定資料行。 它會假設資料行類型為字串。|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|表示提供者支援的特定資料行。 喜歡 PROVIDER_COLUMN_ENTRY_LENGTH，但也可讓您指定資料行的資料類型，以及大小。|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|表示提供者支援的特定資料行。 它會假設資料行類型是 Unicode 字元字串。|  
  
### <a name="schema-rowset-macros"></a>結構描述資料列集巨集  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|標記結構描述對應的開頭。|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|關聯類別的 GUID。|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|結束標記的結構描述對應。|  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 提供者範本參考](../../data/oledb/ole-db-provider-templates-reference.md)
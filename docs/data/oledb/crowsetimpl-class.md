---
title: "CRowsetImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl"
  - "ATL.CRowsetImpl"
  - "ATL::CRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowsetImpl 類別"
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CRowsetImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供標準 OLE DB 資料列集實作，而不需要許多實作介面的多重繼承。  
  
## 語法  
  
```  
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl < T, IRowset >   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### 參數  
 `T`  
 衍生自 `CRowsetImpl`的類別。  
  
 `Storage`  
 使用者資料錄類別。  
  
 `CreatorClass`  
 這個類別包含資料列集的屬性;一般命令。  
  
 `ArrayType`  
 成資料列集的資料儲存區的類別。  這個參數預設為 `CAtlArray`，不過，它可以是支援所需的功能的類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|從 **DBID** 和複本擷取字串至傳遞的 `bstr` 。|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|在兩個資料驗證和儲存 **DBID**的 \([m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)\)。|  
  
### 可覆寫的方法  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|擷取特定用戶端要求的行資訊。|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|檢查任一或兩個參數是否包含字串值，如果是，複製字串值給資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|會檢查看任一或兩個 **DBID**s 包含字串值，如果是，複製給它的資料成員 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|根據預設，在使用者資料錄樣板引數 templatizes 至 `CRowsetImpl`的 `CAtlArray` 。  另一個陣列型別類別可以藉由變更 `ArrayType` 樣板引數使用到 `CRowsetImpl`。|  
|[m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|包含資料列集的初始命令。|  
|[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|包含資料列集的起始索引。|  
  
## 備註  
 以靜態向上轉型的形式，提供`CRowsetImpl` 覆寫。  方法控制特定資料列集將驗證命令文字的方式。  您可以將多個繼承的實作介面來建立自己的 `CRowsetImpl`樣式類別。  您必須提供實作的唯一方法是 **Execute**。  視您建立的資料列集，建立者方法會預期 **Execute**的簽章不同。  例如，如果您使用， `CRowsetImpl`\) 實作的衍生類別結構描述資料列集， **Execute** 方法將具有下列簽章:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 如果您建立 `CRowsetImpl`\) 實作的衍生類別命令或工作階段的資料列集， **Execute** 方法將具有下列簽章:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 實作任何 `CRowsetImpl`衍生的 **Execute** 方法，您必須填入您的內部資料緩衝區 \([m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)\)。  
  
## 需求  
 **Header:** atldb.h
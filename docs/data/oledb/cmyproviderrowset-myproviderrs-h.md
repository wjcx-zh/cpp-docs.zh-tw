---
title: "CMyProviderRowset (MyProviderRS.H) | Microsoft Docs"
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
  - "cmyproviderrowset"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderRS.H 中的 CMyProviderRowset 類別"
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderRowset (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

精靈會替資料列集物件產生一個項目。  在此種情況下，稱為 `CMyProviderRowset`。  `CMyProviderRowset` 類別繼承自名為 `CRowsetImpl` 的 OLE DB 提供者類別，該提供者類別實作資料列集物件的所有必要介面。  下列程式碼顯示了 `CRowsetImpl` 的繼承鏈結：  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl` 也會使用 `IAccessor` 和 `IColumnsInfo` 介面。  它會為資料表的輸出欄位使用這些介面。  類別也提供 **IRowsetIdentity** 的實作，可以讓消費者判斷兩列資料列是否完全相同。  `IRowsetInfo` 介面可實作資料列集物件的屬性。  **IConvertType** 介面可讓提供者解析消費者要求資料型別和提供者使用資料型別的差異。  
  
 `IRowset` 介面實際上會處理資料擷取。  消費者會先呼叫 `GetNextRows` 方法，將控制代碼傳回名為 **HROW** 的資料。  接著，消費者會以 **HROW** 呼叫 **IRowset::GetData**，以擷取要求資料。  
  
 `CRowsetImpl` 也會用到多個樣板參數。  這些參數可讓您決定 `CRowsetImpl` 類別如何處理資料。  `ArrayType` 引數可讓您決定使用何種儲存機制來儲存資料列資料。  **RowClass** 參數會指定何種類別包含 **HROW**。  
  
 **RowsetInterface** 參數讓您也可使用 `IRowsetLocate` 或 `IRowsetScroll` 介面。  `IRowsetLocate` 和 `IRowsetScroll` 介面這兩者都是繼承自 `IRowset`。  因此，OLE DB 提供者樣板必須針對這些介面提供特殊處理。  如果您要使用這些介面的其中一個，就需要使用這個參數。  
  
## 請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
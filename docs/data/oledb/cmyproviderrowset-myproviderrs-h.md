---
title: "CMyProviderRowset (MyProviderRS.H) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 702a86d600a1ff3623ce86c1ad36da9b15876c61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
精靈會產生資料列集物件的項目。 在此種情況下，稱為 `CMyProviderRowset`。 `CMyProviderRowset`類別繼承自呼叫 OLE DB 提供者類別`CRowsetImpl`，它會實作所有必要的介面，如資料列集物件。 下列程式碼示範的繼承鏈結`CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl`也會使用`IAccessor`和`IColumnsInfo`介面。 它會使用這些介面的輸出資料表中的欄位。 這個類別也會提供實作**IRowsetIdentity**，可讓取用者判斷兩個資料列是否相同。 `IRowsetInfo`介面會實作資料列集物件的屬性。 **IConvertType**介面可讓提供者來解決取用者要求的資料類型與所使用的提供者之間的差異。  
  
 `IRowset`介面實際上會處理資料擷取。 取用者會先呼叫方法，稱為`GetNextRows`要傳回的控制代碼的資料列，又稱為**HROW**。 取用者再呼叫**irowset:: Getdata**與**HROW**擷取要求的資料。  
  
 `CRowsetImpl`也會採用數個範本參數。 這些參數可讓您判斷如何`CRowsetImpl`類別會處理資料。 `ArrayType`引數可讓您判斷何種儲存機制用來儲存資料列資料。 **RowClass**參數會指定哪些類別包含**HROW**。  
  
 **RowsetInterface**參數可讓您也使用`IRowsetLocate`或`IRowsetScroll`介面。 `IRowsetLocate`和`IRowsetScroll`兩者均繼承自介面`IRowset`。 因此，OLE DB 提供者範本必須針對這些介面提供特殊處理。 如果您想要使用這些介面，您需要使用這個參數。  
  
## <a name="see-also"></a>請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
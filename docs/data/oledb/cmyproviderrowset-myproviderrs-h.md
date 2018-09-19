---
title: CMyProviderRowset (MyProviderRS.H) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c7c9830970f6e09d1993ac2fd78510b84068efaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021264"
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)

精靈會產生資料列集物件的項目。 在此種情況下，稱為 `CMyProviderRowset`。 `CMyProviderRowset`類別繼承自呼叫 OLE DB 提供者類別`CRowsetImpl`，它會實作所有必要的介面，資料列集物件。 下列程式碼顯示的繼承鏈結`CRowsetImpl`:  
  
```cpp  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
`CRowsetImpl` 也會使用`IAccessor`和`IColumnsInfo`介面。 它會使用這些介面的輸出資料表中的欄位。 類別也會提供實作`IRowsetIdentity`，可讓取用者，以判斷兩個資料列是否相同。 `IRowsetInfo`介面會實作資料列集物件的屬性。 `IConvertType`介面可讓提供者來解決取用者要求的資料類型與所使用的提供者之間的差異。  
  
`IRowset`介面實際上會處理資料擷取。 取用者會先呼叫一個方法，叫做`GetNextRows`傳回的控制代碼的資料列，稱為`HROW`。 取用者接著會呼叫`IRowset::GetData`該`HROW`擷取要求的資料。  
  
`CRowsetImpl` 也會採用數個範本參數。 這些參數可讓您決定如何`CRowsetImpl`類別會處理資料。 `ArrayType`引數可讓您判斷何種儲存機制用來儲存資料列資料。 *RowClass*參數會指定哪個類別包含`HROW`。  
  
*RowsetInterface*參數可讓您同時使用`IRowsetLocate`或`IRowsetScroll`介面。 `IRowsetLocate`並`IRowsetScroll`都繼承自介面`IRowset`。 因此，OLE DB 提供者範本必須針對這些介面提供特殊處理。 如果您想要使用這些介面，您需要使用此參數。  
  
## <a name="see-also"></a>另請參閱  

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
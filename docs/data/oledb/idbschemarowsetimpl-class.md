---
title: IDBSchemaRowsetImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 21910a85dfecf6bd1e66b4ce0df366e3841f3c36
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572251"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 類別
提供結構描述資料列集的實作。  
  
## <a name="syntax"></a>語法

```cpp
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
### <a name="parameters"></a>參數  
 *SessionClass*  
 繼承自 `IDBSchemaRowsetImpl` 的類別。 一般而言，此類別會是使用者的工作階段類別。 

## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CheckRestrictions](#checkrestrictions)|針對結構描述資料列集檢查限制的有效性。|  
|[CreateSchemaRowset](#createschemarowset)|為範本參數所指定的物件實作 COM 物件建立者函式。|  
|[SetRestrictions](#setrestrictions)|指定您在特定結構描述資料列集上支援的限制。|  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetRowset](#getrowset)|傳回結構描述資料列集。|  
|[GetSchemas](#getschemas)|傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。|  
  
## <a name="remarks"></a>備註  
 這個類別會實作[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))介面和範本化的建立者函式[CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)。  
  
 OLE DB 使用結構描述資料列集，傳回提供者內部資料的相關資料。 這類資料通常稱為「中繼資料」。 根據預設，提供者必須一律支援`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，並`DBSCHEMA_PROVIDER_TYPES`所述，在[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程式設計人員參考*。 結構描述資料列集是在結構描述對應中指定。 如需結構描述對應項目的資訊，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)。  
  
 [ATL 物件精靈] 中的 [OLE DB 提供者精靈] 會自動為您專案中的結構描述資料列集產生程式碼 (根據預設，此精靈支援上述的必要結構描述資料列集)。當您使用 [ATL 物件精靈] 建立消費者時，此精靈會使用結構描述資料列集，將正確的資料繫結至提供者。 如果您未實作結構描述資料列集以提供正確的中繼資料，此精靈將不會繫結正確的資料。  
  
 如需如何在提供者內支援結構描述資料列集的資訊，請參閱 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 如需結構描述資料列集的詳細資訊，請參閱 *＜OLE DB 程式設計人員參考＞* 中的 [Schema Rowsets(結構描述資料列集)](/previous-versions/windows/desktop/ms712921\(v=vs.85\))。  

## <a name="checkrestrictions"></a> Idbschemarowsetimpl:: Checkrestrictions
針對結構描述資料列集檢查限制的有效性。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>參數  
 *rguidSchema*  
 [in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。  
  
 *cRestrictions*  
 [in] 消費者針對結構描述資料列集傳入的限制數目。  
  
 *rgRestrictions*  
 [in] 要設定之限制值的長度 *cRestrictions* 陣列。 如需詳細資訊，請參閱說明*rgRestrictions*中的參數[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。  
  
### <a name="remarks"></a>備註  
 使用 `CheckRestrictions` 針對結構描述資料列集檢查限制的有效性。 它會檢查的限制`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`結構描述資料列。 呼叫它來判斷如果取用者呼叫`IDBSchemaRowset::GetRowset`正確無誤。 如果您想要支援與以上所列不同的結構描述資料列集，您應該建立自己的函式來執行這項工作。  
  
 `CheckRestrictions` 如果正在呼叫取用者會決定[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)的正確限制和正確限制類型 (例如，字串 VT_BSTR) 提供者支援。 它也會判斷是否支援正確的限制數目。 根據預設， `CheckRestrictions` 會透過 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 呼叫，來詢問提供者有關它在指定資料列集上支援的限制。 接著，它會將來自消費者的限制與提供者支援的限制進行比較，以判斷其為成功或失敗。  
  
 如需有關結構描述資料列集的詳細資訊，請參閱 < [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程式設計人員參考*Windows SDK 中。  

## <a name="createschemarowset"></a> Idbschemarowsetimpl:: Createschemarowset
為範本參數所指定的物件實作 COM 物件建立者函式。  
  
### <a name="syntax"></a>語法  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>參數  
 *pUnkOuter*  
 [in]為外部[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)彙總時，否則為 NULL。  
  
 *cRestrictions*  
 [in] 套用至結構描述資料列集的限制計數。  
  
 *rgRestrictions*  
 [in] 要套用至資料列集的 `cRestrictions`**VARIANT**陣列。  
  
 *riid*  
 [in]介面，以[QueryInterface](../../atl/queryinterface.md)的輸出上`IUnknown`。  
  
 *cPropertySets*  
 [in] 要設定的屬性集數目。  
  
 *rgPropertySets*  
 [in]陣列[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))指定要設定之屬性的結構。  
  
 *ppRowset*  
 [out]外寄`IUnknown`要求*riid*。 這`IUnknown`是結構描述資料列集物件上的介面。  
  
 *pSchemaRowset*  
 [out] 結構描述資料列集類別執行個體的指標。 一般而言，您不會使用此參數；但如果您必須對結構描述資料列集執行更多工作，才能送出至 COM 物件，則可以使用此參數。 存留期*pSchemaRowset*繫結*Pprowset&lt*。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此函式會對所有類型的結構描述資料列集實作一般建立者。 一般而言，使用者不會呼叫此函式， 而是由結構描述對應的實作進行呼叫。 

## <a name="setrestrictions"></a> Idbschemarowsetimpl:: Setrestrictions
指定您在特定結構描述資料列集上支援的限制。  
  
### <a name="syntax"></a>語法  
  
```cpp
void SetRestrictions(ULONG cRestrictions,  
   GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>參數  
 *cRestrictions*  
 [in]中的限制數目*rgRestrictions* array 和 Guid 中數目*rguidSchema*陣列。  
  
 *rguidSchema*  
 [in] 要擷取限制之目標結構描述資料列集的 GUID 陣列。 每個陣列元素包含一個結構描述資料列集的 GUID (例如 `DBSCHEMA_TABLES`)。  
  
 *rgRestrictions*  
 [in] 要設定之限制值的長度 *cRestrictions* 陣列。 每個元素會對應至 GUID 所識別之結構描述資料列集上的限制。 如果提供者不支援結構描述資料列集，此元素會設定為零。 否則， **ULONG** 值會包含代表該結構描述資料列集支援之限制的位元遮罩。 在其的限制對應至特定的結構描述資料列集的詳細資訊，請參閱結構描述資料列集 Guid 的資料表中[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程式設計人員參考*在 Windows 中SDK。  
  
### <a name="remarks"></a>備註  
 `IDBSchemaRowset`物件會呼叫`SetRestrictions`支援特定的結構描述資料列集來判斷哪些限制 (它會呼叫[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)透過向上轉型的指標)。 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。  
  
 這個方法的預設實作會設定*rgRestrictions*陣列項目設為 0。 您可以覆寫工作階段類別中的預設，將限制設定為非預設。  
  
 如需實作結構描述資料列集支援的資訊，請參閱 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)。  
  
 如需支援結構描述資料列集提供者的範例，請參閱 < [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例。  
  
 如需有關結構描述資料列集的詳細資訊，請參閱 < [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))中*OLE DB 程式設計人員參考*Windows SDK 中。 
  
## <a name="getrowset"></a> Idbschemarowsetimpl:: Getrowset
傳回結構描述資料列集。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>參數  
 *pUnkOuter*  
 [in]為外部`IUnknown`時彙總，否則為 NULL。  
  
 *rguidSchema*  
 [in] 所要求之結構描述資料列集 GUID 的參考 (例如 `DBSCHEMA_TABLES`)。  
  
 *cRestrictions*  
 [in] 要套用至資料列集的限制計數。  
  
 *rgRestrictions*  
 [in] 代表限制的 `cRestrictions`**VARIANT**陣列。  
  
 *riid*  
 [in] 新建立之結構描述資料列集的要求 IID。  
  
 *cPropertySets*  
 [in] 要設定的屬性集數目。  
  
 *rgPropertySets*  
 [輸入/輸出]陣列[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構，以在新建立的結構描述資料列集上設定。  
  
 *ppRowset*  
 [out] 新建立之結構描述資料列集上所要求的介面指標。  
  
### <a name="remarks"></a>備註  
 此方法需要使用者具有工作階段類別中的結構描述對應。 使用結構描述對應資訊`GetRowset`會建立指定資料列集物件，如果*rguidSchema*參數等於其中一個對應項目 Guid。 如需對應項目的說明，請參閱 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) 。  
  
 請參閱[idbschemarowset:: Getrowset](/previous-versions/windows/desktop/ms722634\(v=vs.85\)) Windows SDK 中。  

## <a name="getschemas"></a> Idbschemarowsetimpl:: Getschemas
傳回 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)可存取的結構描述資料列集清單。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest);  
```  
  
#### <a name="parameters"></a>參數  
 *pcSchemas*  
 [out] 要填入結構描述數目的 **ULONG** 指標。  
  
 *prgSchemas*  
 [out] 要填入結構描述資料列集 GUID 陣列指標的 GUID 陣列指標。  
  
 *prgRest*  
 [out] 要填入限制陣列的 **ULONG**陣列指標。  
  
### <a name="remarks"></a>備註  
 此方法會傳回提供者支援之所有結構描述資料列集的陣列。 請參閱[idbschemarowset:: Getschemas](/previous-versions/windows/desktop/ms719605\(v=vs.85\)) Windows SDK 中。  
  
 此函式的實作需要使用者具有工作階段類別中的結構描述對應。 藉由使用此結構描述對應資訊，它就能接著以對應中結構描述的 GUID 陣列來回應。 這會是提供者支援的結構描述。  

## <a name="see-also"></a>另請參閱  
 [IDBSchemaRowsetImpl 類別成員](http://msdn.microsoft.com/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [支援結構描述資料列集](../../data/oledb/supporting-schema-rowsets.md)    
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)    
 [UpdatePV](../../visual-cpp-samples.md)
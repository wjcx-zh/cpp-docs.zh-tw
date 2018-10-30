---
title: CCustomSource (CustomDS.H) |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3ad9a2c9ac2d7371cc1fb357e2ce6a9e35701607
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216379"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS.h)

提供者類別會使用多重繼承。 下列程式碼顯示資料來源物件的繼承鏈結：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

所有 COM 元件會都衍生自`CComObjectRootEx`和`CComCoClass`。 `CComObjectRootEx` 提供所有實作`IUnknown`介面。 它可以處理任何執行緒模型。 `CComCoClass` 處理所需的任何錯誤支援。 如果您想要更豐富的錯誤資訊傳送給用戶端，您可以使用一些錯誤 Api 中`CComCoClass`。

資料來源物件也會繼承來自數個 'Impl' 類別。 每個類別會提供介面的實作。 資料來源物件實作`IPersist`， `IDBProperties`， `IDBInitialize`，和`IDBCreateSession`介面。 每個介面會實作所需 OLE db 資料來源物件。 您可以選擇支援或不支援繼承或不繼承自其中一個 'Impl' 類別的特定功能。 如果您想要支援`IDBDataSourceAdmin`介面，繼承自`IDBDataSourceAdminImpl`類別，以取得所需的功能。

## <a name="com-map"></a>COM 對應

每當用戶端呼叫`QueryInterface`對於資料來源上的介面，它會經歷下列 COM 對應：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

所有 COM 元件會都衍生自`CComObjectRootEx`和`CComCoClass`。 `CComObjectRootEx` 提供所有實作`IUnknown`介面。 它可以處理任何執行緒模型。 `CComCoClass` 處理所需的任何錯誤支援。 如果您想要更豐富的錯誤資訊傳送給用戶端，您可以使用一些錯誤 Api 中`CComCoClass`。

資料來源物件也會繼承來自數個 'Impl' 類別。 每個類別會提供介面的實作。 資料來源物件實作`IPersist`， `IDBProperties`， `IDBInitialize`，和`IDBCreateSession`介面。 每個介面會實作所需 OLE db 資料來源物件。 您可以選擇支援或不支援繼承或不繼承自其中一個 'Impl' 類別的特定功能。 如果您想要支援`IDBDataSourceAdmin`介面，繼承自`IDBDataSourceAdminImpl`類別，以取得所需的功能。

## <a name="com-map"></a>COM 對應

每當用戶端呼叫`QueryInterface`對於資料來源上的介面，它會經歷下列 COM 對應：

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 巨集是從 ATL，並表達的實作`QueryInterface`在`CComObjectRootEx`傳回適當的介面。

## <a name="property-map"></a>屬性對應

屬性對應指定的提供者所指派的所有屬性：

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

OLE DB 中的屬性分組。 資料來源物件具有兩個群組的屬性： 一個用於 DBPROPSET_DATASOURCEINFO 設定，另一個用於 DBPROPSET_DBINIT 設定。 DBPROPSET_DATASOURCEINFO 集對應至提供者和其資料來源相關的屬性。 DBPROPSET_DBINIT 集對應至在初始化時使用的屬性。 OLE DB 提供者範本處理這些 PROPERTY_SET 巨集的集合。 巨集來建立包含的屬性陣列的區塊。 每當用戶端呼叫`IDBProperties`介面，提供者使用的屬性對應。

您不需要實作規格中的每個屬性。 不過，您必須支援所需的屬性;如需詳細資訊層級 0 一致性規格，請參閱。 如果您不想要支援的屬性，您可以從對應移除它。 如果您想要支援的屬性，將它加入至地圖使用 PROPERTY_INFO_ENTRY 巨集。 巨集對應於`UPROPINFO`結構，如下列程式碼所示：

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

在結構中的每個項目表示處理屬性的資訊。 它包含`DBPROPID`判斷 GUID 和 ID 的屬性。 它也會包含項目，以判斷型別和屬性的值。

如果您想要變更預設屬性的值 （請注意，取用者可以隨時變更可寫入屬性的值），您可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 巨集。 這些巨集可讓您指定的對應屬性的值。 PROPERTY_INFO_ENTRY_VALUE 巨集是縮寫標記法，可讓您變更的值。 PROPERTY_INFO_ENTRY_VALUE 巨集呼叫 PROPERTY_INFO_ENTRY_EX 巨集。 這個巨集可讓您新增或變更中屬性的所有`UPROPINFO`結構。

如果您想要定義您自己的屬性集，您可以加入一個藉由其他的 BEGIN_PROPSET_MAP/END_PROPSET_MAP 組合。 定義的屬性集 GUID，然後定義您自己的屬性。 如果您有提供者特有的屬性，請將它們加入新的屬性，而不是使用現有設定。 這可避免更新版本的 OLE DB 中的問題。

## <a name="user-defined-property-sets"></a>使用者定義的屬性集

Visual c + + 支援使用者定義的屬性集。 您不需要覆寫`GetProperties`或`GetPropertyInfo`。 相反地，範本會偵測到任何使用者定義的屬性集，並將它新增至適當的物件。

如果您有必須可在初始化階段的使用者定義的屬性集 (亦即，取用者呼叫之前`IDBInitialize::Initialize`)，您可以指定此使用 UPROPSET_USERINIT 旗標以及 BEGIN_PROPERTY_SET_EX 巨集。 此工作 （如 OLE DB 規格需要） 的資料來源物件必須是屬性集。 例如: 

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>

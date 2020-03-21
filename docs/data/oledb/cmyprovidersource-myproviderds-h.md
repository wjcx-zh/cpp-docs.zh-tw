---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 60324ae914c9490144a715e06323ee6d184ce201
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079728"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource （CustomDS .h）

提供者類別會使用多重繼承。 下列程式碼顯示資料來源物件的繼承鏈：

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

所有 COM 元件都衍生自 `CComObjectRootEx` 和 `CComCoClass`。 `CComObjectRootEx` 提供 `IUnknown` 介面的所有執行。 它可以處理任何執行緒模型。 `CComCoClass` 會處理所需的任何錯誤支援。 如果您想要將更豐富的錯誤資訊傳送給用戶端，您可以在 `CComCoClass`中使用一些錯誤 Api。

資料來源物件也會繼承自數個 ' Impl ' 類別。 每個類別都會提供介面的執行。 資料來源物件會執行 `IPersist`、`IDBProperties`、`IDBInitialize`和 `IDBCreateSession` 介面。 OLE DB 需要每個介面，才能執行資料來源物件。 您可以藉由繼承或不繼承自這些 ' Impl ' 類別的其中一個，來選擇支援或不支援特定功能。 如果您想要支援 `IDBDataSourceAdmin` 介面，則會繼承自 `IDBDataSourceAdminImpl` 類別，以取得所需的功能。

## <a name="com-map"></a>COM 對應

每當用戶端針對資料來源上的介面呼叫 `QueryInterface` 時，就會經歷下列 COM 對應：

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

所有 COM 元件都衍生自 `CComObjectRootEx` 和 `CComCoClass`。 `CComObjectRootEx` 提供 `IUnknown` 介面的所有執行。 它可以處理任何執行緒模型。 `CComCoClass` 會處理所需的任何錯誤支援。 如果您想要將更豐富的錯誤資訊傳送給用戶端，您可以在 `CComCoClass`中使用一些錯誤 Api。

資料來源物件也會繼承自數個 ' Impl ' 類別。 每個類別都會提供介面的執行。 資料來源物件會執行 `IPersist`、`IDBProperties`、`IDBInitialize`和 `IDBCreateSession` 介面。 OLE DB 需要每個介面，才能執行資料來源物件。 您可以藉由繼承或不繼承自這些 ' Impl ' 類別的其中一個，來選擇支援或不支援特定功能。 如果您想要支援 `IDBDataSourceAdmin` 介面，則會繼承自 `IDBDataSourceAdminImpl` 類別，以取得所需的功能。

## <a name="com-map"></a>COM 對應

每當用戶端針對資料來源上的介面呼叫 `QueryInterface` 時，就會經歷下列 COM 對應：

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 宏來自 ATL，並告訴 `QueryInterface` 在 `CComObjectRootEx` 中的執行，以傳回適當的介面。

## <a name="property-map"></a>屬性對應

屬性對應會指定提供者指派的所有屬性：

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

OLE DB 中的屬性會分組。 資料來源物件有兩個屬性群組：一個用於 DBPROPSET_DATASOURCEINFO 集，另一個用於 DBPROPSET_DBINIT 集。 DBPROPSET_DATASOURCEINFO 集合會對應至提供者及其資料來源的屬性。 DBPROPSET_DBINIT 集會對應到在初始化時使用的屬性。 OLE DB 提供者範本會使用 PROPERTY_SET 宏來處理這些集合。 宏會建立包含屬性陣列的區塊。 每當用戶端呼叫 `IDBProperties` 介面時，提供者會使用屬性對應。

您不需要執行規格中的每個屬性。 不過，您必須支援所需的屬性;如需詳細資訊，請參閱層級0一致性規格。 如果您不想要支援屬性，可以將它從對應中移除。 如果您想要支援屬性，請使用 PROPERTY_INFO_ENTRY 宏將其加入至對應。 宏會對應至 `UPROPINFO` 結構，如下列程式碼所示：

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

結構中的每個元素都代表處理屬性的資訊。 它包含 `DBPROPID` 來判斷屬性的 GUID 和識別碼。 它也包含專案，以判斷屬性的類型和值。

如果您想要變更屬性的預設值（請注意，取用者隨時可以變更可寫入屬性的值），您可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 宏。 這些宏可讓您指定對應屬性的值。 PROPERTY_INFO_ENTRY_VALUE 宏是一個簡短的標記法，可讓您變更此值。 PROPERTY_INFO_ENTRY_VALUE 宏會呼叫 PROPERTY_INFO_ENTRY_EX 宏。 這個宏可讓您加入或變更 `UPROPINFO` 結構中的所有屬性。

如果您想要定義自己的屬性集，可以藉由建立額外的 BEGIN_PROPSET_MAP/END_PROPSET_MAP 組合來加入一個。 定義屬性集的 GUID，然後定義您自己的屬性。 如果您有提供者專屬的屬性，請將它們新增至新的屬性集，而不是使用現有的。 這可避免較新版本 OLE DB 中的問題。

## <a name="user-defined-property-sets"></a>使用者定義的屬性集

Visual C++支援使用者定義的屬性集。 您不需要覆寫 `GetProperties` 或 `GetPropertyInfo`。 相反地，範本會偵測任何使用者定義的屬性集，並將它新增至適當的物件。

如果您的使用者定義屬性集必須在初始化時使用（也就是在取用者呼叫 `IDBInitialize::Initialize`之前），您可以使用 UPROPSET_USERINIT 旗標以及 BEGIN_PROPERTY_SET_EX 宏來指定此屬性。 屬性集必須在資料來源物件中，才能讓此作業正常執行（如 OLE DB 規格所需）。 例如：

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>

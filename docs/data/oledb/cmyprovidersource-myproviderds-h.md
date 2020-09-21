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
ms.openlocfilehash: 8e92c30e8d62ade095167880917ad70da8e59b36
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742914"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (Customds.h) 

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

所有 COM 元件都是衍生自 `CComObjectRootEx` 和 `CComCoClass` 。 `CComObjectRootEx` 提供介面的所有執行 `IUnknown` 。 它可以處理任何執行緒模型。 `CComCoClass` 處理所需的任何錯誤支援。 如果您想要將更豐富的錯誤資訊傳送給用戶端，您可以使用中的一些錯誤 Api `CComCoClass` 。

資料來源物件也會繼承自數個 ' Impl ' 類別。 每個類別都會提供介面的實作為。 資料來源物件會實行 `IPersist` 、、 `IDBProperties` `IDBInitialize` 和 `IDBCreateSession` 介面。 OLE DB 需要每個介面來執行資料來源物件。 您可以藉由繼承或不繼承這些 ' Impl ' 類別的其中之一，來選擇支援或不支援特定功能。 如果您想要支援 `IDBDataSourceAdmin` 介面，您可以從類別繼承， `IDBDataSourceAdminImpl` 以取得所需的功能。

## <a name="com-map"></a>COM 對應

每當用戶端呼叫 `QueryInterface` 資料來源上的介面時，它就會經歷下列 COM 對應：

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 宏來自 ATL，並告知中的實傳回 `QueryInterface` `CComObjectRootEx` 適當的介面。

## <a name="property-map"></a>屬性對應

屬性對應會指定提供者所指派的所有屬性：

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

OLE DB 中的屬性會進行分組。 資料來源物件有兩個屬性群組：一個用於 DBPROPSET_DATASOURCEINFO 集，一個用於 DBPROPSET_DBINIT 集。 DBPROPSET_DATASOURCEINFO 設定對應至提供者和其資料來源的相關屬性。 DBPROPSET_DBINIT 設定會對應到初始化時使用的屬性。 OLE DB 提供者範本會使用 PROPERTY_SET 宏來處理這些集合。 宏會建立包含屬性陣列的區塊。 每當用戶端呼叫 `IDBProperties` 介面時，提供者就會使用屬性對應。

您不需要在規格中執行每個屬性。 不過，您必須支援所需的屬性;如需詳細資訊，請參閱層級0一致性規格。 如果您不想要支援屬性，您可以從對應中移除它。 如果您想要支援屬性，請使用 PROPERTY_INFO_ENTRY 宏將其加入至對應。 宏會對應至 `UPROPINFO` 結構，如下列程式碼所示：

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

結構中的每個元素都代表處理屬性的資訊。 它包含 `DBPROPID` 可判斷屬性之 GUID 和識別碼的。 它也包含用來判斷屬性之類型和值的專案。

如果您想要變更屬性的預設值 (請注意，取用者可以隨時變更可寫入屬性的值) ，您可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 宏。 這些宏可讓您指定對應屬性的值。 PROPERTY_INFO_ENTRY_VALUE 宏是可讓您變更值的縮寫標記法。 PROPERTY_INFO_ENTRY_VALUE 宏會呼叫 PROPERTY_INFO_ENTRY_EX 宏。 這個宏可讓您在結構中加入或變更所有屬性 `UPROPINFO` 。

如果您想要定義您自己的屬性集，可以藉由建立額外的 BEGIN_PROPSET_MAP/END_PROPSET_MAP 組合來新增一個屬性集。 定義屬性集的 GUID，然後定義您自己的屬性。 如果您有提供者專屬的屬性，請將它們新增至新的屬性集，而不是使用現有的屬性集。 這可避免 OLE DB 的較新版本發生問題。

## <a name="user-defined-property-sets"></a>使用者定義的屬性集

Visual C++ 支援使用者定義的屬性集。 您不必覆寫 `GetProperties` 或 `GetPropertyInfo` 。 相反地，範本會偵測任何使用者定義的屬性集，並將它新增至適當的物件。

如果您有需要在初始化時使用的使用者定義屬性集 (也就是在取用者呼叫) 之前， `IDBInitialize::Initialize` 您可以使用 UPROPSET_USERINIT 旗標以及 BEGIN_PROPERTY_SET_EX 宏來指定此屬性。 屬性集必須在資料來源物件中，才能運作 (因為 OLE DB 規格需要) 。 例如：

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>另請參閱

[提供者 Wizard 產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>

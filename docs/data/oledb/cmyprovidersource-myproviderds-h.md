---
title: "CMyProviderSource (MyProviderDS.H) | Microsoft Docs"
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
  - ""myproviderds.h""
  - "cmyprovidersource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderDS.H 中的 CMyProviderSource 類別"
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSource (MyProviderDS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供者類別使用多重繼承。  下列程式碼顯示資料來源物件的繼承鏈結：  
  
```  
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 所有 COM 元件都衍生自 `CComObjectRootEx` 和 `CComCoClass`。  `CComObjectRootEx` 提供所有 **IUnknown** 介面的實作。  它可以處理任何執行緒模型。  `CComCoClass` 則能處理任何需要的錯誤支援。  若想將更豐富的錯誤資訊傳送至用戶端，您可使用 `CComCoClass` 的某些錯誤 API。  
  
 資料來源物件也會繼承自多個 'Impl' 類別。  每個類別都提供介面的實作。  資料來源物件會實作 `IPersist`、`IDBProperties`、**IDBInitialize** 和 **IDBCreateSession** 介面。  OLE DB 需要用到每個介面來實作資料來源物件。  您可選擇繼承或不繼承這些 'Impl' 類別之一，來支援或不支援特定的功能。  如果想要支援 **IDBDataSourceAdmin** 介面，您可繼承自 **IDBDataSourceAdminImpl** 類別，以得到所需功能。  
  
## COM 對應  
 每當用戶端為資料來源的介面呼叫 `QueryInterface` 時，就會瀏覽下列 COM 對應：  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 來自 ATL 的 COM\_INTERFACE\_ENTRY 巨集，會通知 `CComObjectRootEx` 內的 `QueryInterface` 實作傳回適當的介面。  
  
## 屬性對應  
 屬性對應指定了提供者所指定的所有屬性：  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
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
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 OLE DB 內的屬性將予以群組分類。  資料來源物件擁有兩個屬性群組：一個是針對 **DBPROPSET\_DATASOURCEINFO** 集合，一個則針對 **DBPROPSET\_DBINIT** 集合。  **DBPROPSET\_DATASOURCEINFO** 集合對應到提供者和資料來源的屬性。  **DBPROPSET\_DBINIT** 集合對應到初始化時所使用的屬性。  OLE DB 提供者樣板會以 PROPERTY\_SET 巨集來處理這些集合。  巨集會建立一包含屬性陣列的區塊。  每當用戶端呼叫 `IDBProperties` 介面時，提供者都會使用屬性對應。  
  
 您不需要實作規格內的每個屬性。  不過，您必須支援所需的屬性，如需詳細資訊，請參閱層級 0 的一致性規格。  若您不想支援某屬性，可從對應中將它移除。  若您要支援某屬性，可使用 PROPERTY\_INFO\_ENTRY 巨集將它加入至對應。  此巨集會依下列程式碼對應至 **UPROPINFO** 結構：  
  
```  
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
  
 結構中的每個項目都代表可處理屬性的資訊。  它包含一個可決定屬性之 GUID 和 ID 的 **DBPROPID**。  它也包含可決定屬性型別和數值的項目。  
  
 如果您想變更屬性的預設值 \(請注意，消費者能夠隨時變更可寫入屬性的數值\)，您可使用 PROPERTY\_INFO\_ENTRY\_VALUE 或 PROPERTY\_INFO\_ENTRY\_EX 巨集。  這些巨集可讓您為對應的屬性指定數值。  PROPERTY\_INFO\_ENTRY\_VALUE 巨集是可允許變更數值的簡略標記法。  PROPERTY\_INFO\_ENTRY\_VALUE 巨集會呼叫 PROPERTY\_INFO\_ENTRY\_EX 巨集。  此巨集可讓您加入或變更 **UPROPINFO** 結構內的所有屬性。  
  
 若要定義自己的屬性集 \(Property Set\)，您可建立額外的 BEGIN\_PROPSET\_MAP\/END\_PROPSET\_MAP 組合來加入屬性集。  您需要為屬性集定義 GUID，然後定義自己的屬性。  若您擁有提供者專用的屬性，請將它們加入新的屬性集內，而非使用現有的屬性集。  如此可避免在較新版的 OLE DB 中發生問題。  
  
## 使用者定義的屬性集  
 Visual C\+\+ .NET 可支援使用者定義的屬性集 \(Property Set\)。  您不再需要覆寫 **GetProperties** 或 `GetPropertyInfo`。  相反地，樣板會偵測到任何使用者定義的屬性集，並將它加入至適當的物件。  
  
 若您擁有使用者定義的屬性集，而它必須可以在初始化階段使用 \(也就是在消費者呼叫 **IDBInitialize::Initialize** 之前\)，就可使用 **UPROPSET\_USERINIT** 旗標搭配 BEGIN\_PROPERTY\_SET\_EX 巨集來指定它。  屬性集必須位於資料來源物件內，才能使用此種作法 \(如 OLE DB 規格所要求的\)。  例如：  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## 請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
---
title: CDataSource 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: 2564d4d9b0a2e5df1f575d6f2627ce80f48533c1
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021913"
---
# <a name="cdatasource-class"></a>CDataSource 類別

對應至 OLE DB 資料來源物件，其表示透過提供者與資料來源的連線。

## <a name="syntax"></a>語法

```cpp
class CDataSource
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[關閉](#close)|關閉連線。|
|[GetInitializationString](#getinitializationstring)|擷取目前開啟之資料來源的初始化字串。|
|[GetProperties](#getproperties)|取得目前針對所連線之資料來源設定的屬性值。|
|[GetProperty](#getproperty)|取得目前針對所連線資料來源設定的單一屬性值。|
|[開啟](#open)|建立使用提供者 （資料來源） 的連線`CLSID`， `ProgID`，或`CEnumerator`呼叫端提供的 moniker。|
|[OpenFromFileName](#openfromfilename)|從以使用者提供的檔名指定的檔案，開啟資料來源。|
|[OpenFromInitializationString](#openfrominitializationstring)|開啟以初始化字串指定的資料來源。|
|[OpenWithPromptFileName](#openwithpromptfilename)|允許使用者選取先前建立的資料連結檔案，以開啟對應的資料來源。|
|[OpenWithServiceComponents](#openwithservicecomponents)|使用 [資料連結] 對話方塊開啟資料來源物件。|

## <a name="remarks"></a>備註

可為單一連線建立一個或多個資料庫工作階段。 這些工作階段是以 `CSession` 表示。 您必須呼叫[cdatasource:: Open](../../data/oledb/cdatasource-open.md)若要開啟的連接，再建立的工作階段`CSession::Open`。

如需如何使用的範例`CDataSource`，請參閱 < [CatDB](../../overview/visual-cpp-samples.md)範例。

## <a name="close"></a> CDataSource::Close

關閉連接時釋放`m_spInit`指標。

### <a name="syntax"></a>語法

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a> CDataSource::GetInitializationString

擷取目前已開啟的資料來源初始化字串。

### <a name="syntax"></a>語法

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>參數

*pInitializationString*<br/>
[out]初始化字串指標。

*bIncludePassword*<br/>
[in]**真**如果字串包含密碼; 否則為**false**。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

產生的初始化字串可用來在稍後重新開啟此資料來源連接。

## <a name="getproperties"></a> Cdatasource:: Getproperties

傳回所要求的連接的資料來源物件的屬性資訊。

### <a name="syntax"></a>語法

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>參數

請參閱[idbproperties:: Getproperties](/previous-versions/windows/desktop/ms714344(v=vs.85))中*OLE DB 程式設計人員參考*Windows SDK 中。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

若要取得的單一屬性，請使用[GetProperty](../../data/oledb/cdatasource-getproperty.md)。

## <a name="getproperty"></a> Cdatasource:: Getproperty

傳回連接的資料來源物件的指定屬性的值。

### <a name="syntax"></a>語法

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>參數

*guid*<br/>
[in]GUID，識別要傳回之屬性所設定的屬性。

*propid*<br/>
[in]屬性 ID 屬性來傳回。

*pVariant*<br/>
[out]Variant 的指標位置`GetProperty`傳回屬性的值。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

若要取得多個屬性，請使用[GetProperties](../../data/oledb/cdatasource-getproperties.md)。

## <a name="open"></a> Cdatasource:: Open

開啟資料來源使用的連接`CLSID`， `ProgID`，或`CEnumerator`moniker 或以定位程式對話方塊以提示使用者。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>參數

*clsid*<br/>
[in]`CLSID`的資料提供者。

*pPropSet*<br/>
[in]陣列的指標[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構，其中包含要設定屬性和值。 請參閱[的屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))中*OLE DB 程式設計人員參考*Windows SDK 中。

*nPropertySets*<br/>
[in]數目[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構傳入*Dbpropset*引數。

*pName*<br/>
[in] 要連接的資料庫名稱。

*pUserName*<br/>
[in] 使用者的名稱。

*pPassword*<br/>
[in] 使用者的密碼。

*nInitMode*<br/>
[in] 資料庫初始化模式。 請參閱[初始化屬性](/previous-versions/windows/desktop/ms723127(v=vs.85))中*OLE DB 程式設計人員參考*Windows SDK，如需有效初始化模式的清單中。 如果*nInitMode*是零、 任何初始化模式會包含用來開啟連接的屬性集。

*szProgID*<br/>
[in] 程式識別碼。

*enumerator*<br/>
[in]A [CEnumerator](../../data/oledb/cenumerator-class.md)物件，用來取得 moniker，以便開啟連接，當呼叫端未指定`CLSID`。

*hWnd*<br/>
[in] 做為對話方塊之父視窗的控制代碼。 使用會使用函式多載*hWnd*參數都會自動叫用服務元件; 如需詳細資訊，請參閱備註。

*dwPromptOptions*<br/>
[in] 決定要顯示的定位程式對話方塊樣式。 請參閱 Msdasc.h 中的可能值。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

使用的方法多載*hWnd*參數使用 oledb32.dll 中的服務元件開啟資料來源物件; 此 DLL 包含服務元件的功能，例如資源集區的自動實作交易登記等。 如需詳細資訊，請參閱中的 < OLE DB 服務 」 上的 OLE DB 程式設計人員參考[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

請勿使用的方法多載*hWnd*參數開啟資料來源物件，而不使用 oledb32.dll 中的服務元件。 A [CDataSource](../../data/oledb/cdatasource-class.md)使用這些函式多載開啟的物件將無法使用任何服務元件的功能。

### <a name="example"></a>範例

下列程式碼示範如何使用 OLE DB 範本開啟 Jet 4.0 資料來源。 您可以將 Jet 資料來源當做 OLE DB 資料來源。 不過，您呼叫`Open`需要兩個屬性集： 一個用於 DBPROPSET_DBINIT，另一個則用於 DBPROPSET_JETOLEDB_DBINIT，使您可以設定 DBPROP_JETOLEDB_DATABASEPASSWORD。

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

從以使用者提供的檔名指定的檔案，開啟資料來源。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>參數

*szFileName*<br/>
[in] 檔案的名稱，通常是資料來源連接 (.UDL) 檔案。

如需詳細資料連結檔案 （.udl 檔案） 的詳細資訊，請參閱[資料連結 API 概觀](/previous-versions/windows/desktop/ms718102(v=vs.85))Windows SDK 中。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。 如需詳細資訊，請參閱中的 < OLE DB 服務 」 上的 OLE DB 程式設計人員參考[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="openfrominitializationstring"></a> Cdatasource:: Openfrominitializationstring

開啟資料來源的使用者提供的初始化字串所指定。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>參數

*szInitializationString*<br/>
[in]初始化字串。

*fPromptForInfo*<br/>
[in]如果這個引數設定為 **，則為 true**，然後`OpenFromInitializationString`將 DBPROP_INIT_PROMPT 屬性 DBPROMPT_COMPLETEREQUIRED，指定 需要更多資訊時，才會提示使用者。 這是在其中初始化字串會指定資料庫需要密碼的情況下很有用，但是字串不包含密碼。 密碼 （或任何其他遺失的資訊），將會提示使用者嘗試連接至資料庫時。

預設值是**false**，指定使用者永遠不會被提示 （設定 DBPROP_INIT_PROMPT 來 DBPROMPT_NOPROMPT）。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。

## <a name="openwithpromptfilename"></a> CDataSource::OpenWithPromptFileName

此方法會以對話方塊提示使用者，然後使用使用者所指定的檔案開啟資料來源。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>參數

*hWnd*<br/>
[in] 做為對話方塊之父視窗的控制代碼。

*dwPromptOptions*<br/>
[in] 決定要顯示的定位程式對話方塊樣式。 請參閱 Msdasc.h 中的可能值。

*szInitialDirectory*<br/>
[in] 要顯示在定位器對話方塊中的初始目錄。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。 如需詳細資訊，請參閱中的 < OLE DB 服務 」 上的 OLE DB 程式設計人員參考[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="openwithservicecomponents"></a> Cdatasource:: Openwithservicecomponents

使用 oledb32.dll 中的服務元件來開啟資料來源物件。

### <a name="syntax"></a>語法

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>參數

*clsid*<br/>
[in]`CLSID`資料提供者。

*szProgID*<br/>
[in] 資料提供者的程式識別碼。

*pPropset*<br/>
[in]陣列的指標[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構，其中包含要設定屬性和值。 請參閱[的屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))中*OLE DB 程式設計人員參考*Windows SDK 中。 如果資料來源物件已初始化，屬性必須屬於資料來源屬性群組。 如果相同的屬性中指定了一次以上*Dbpropset*，則會使用哪些值是特定提供者。 如果*ulPropSets*為零，會忽略這個參數。

*ulPropSets*<br/>
[in]數目[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構傳入*Dbpropset*引數。 如果這是零，提供者會忽略*Dbpropset*。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。 如需詳細資訊，請參閱中的 < OLE DB 服務 」 上的 OLE DB 程式設計人員參考[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
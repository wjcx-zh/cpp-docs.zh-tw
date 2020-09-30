---
title: CCommand 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 109998dd742828b3c41672fa2afa8716e4687f6a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501013"
---
# <a name="ccommand-class"></a>CCommand 類別

提供用來設定和執行命令的方法。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
存取子類別的類型 (例如 `CDynamicParameterAccessor` ， `CDynamicStringAccessor` 或 `CEnumeratorAccessor` 您想要命令使用的) 。 預設值為 `CNoAccessor` ，指定類別不支援參數或輸出資料行。

*TRowset*<br/>
資料列集類別 (的類型， `CArrayRowset` 例如 `CNoRowset` 您想要命令使用的或) 。 預設值為 `CRowset`。

*TMultiple*<br/>
若要使用可傳回多個結果的 OLE DB 命令，請指定 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否則，請使用 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 如需詳細資訊，請參閱 [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85))。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[關閉](#close)|關閉目前的命令。|
|[GetNextResult](#getnextresult)|使用多個結果集時，提取下一個結果。|
|[開啟](#open)|執行並選擇性地系結命令。|

### <a name="inherited-methods"></a>繼承的方法

| 名稱 | 描述 |
|-|-|
|[建立](#create)|為指定的會話建立新的命令，然後設定命令文字。|
|[CreateCommand](#createcommand)|建立新的命令。|
|[GetParameterInfo](#getparameterinfo)|取得命令參數、其名稱及其類型的清單。|
|[準備](#prepare)|驗證並優化目前的命令。|
|[ReleaseCommand](#releasecommand)|視需要釋放參數存取子，然後釋放命令。|
|[SetParameterInfo](#setparameterinfo)|指定每個命令參數的原生類型。|
|[Unprepare](#unprepare)|捨棄目前的命令執行計畫。|

## <a name="remarks"></a>備註

當您需要執行以參數為基礎的作業或執行命令時，請使用這個類別。 如果您只需要開啟簡單的資料列集，請改用 [CTable](../../data/oledb/ctable-class.md) 。

您所使用的存取子類別會決定系結參數和資料的方法。

請注意，您無法搭配 OLE DB Provider for Jet 使用預存程式，因為該提供者不支援預存程式 () 的查詢字串中只允許常數。

## <a name="ccommandclose"></a><a name="close"></a> CCommand：： Close

釋放與命令相關聯的存取子資料列集。

### <a name="syntax"></a>語法

```cpp
void Close();
```

### <a name="remarks"></a>備註

命令使用資料列集、結果集存取子， (選擇性地) 參數存取子， (不同于不支援參數，且不需要參數存取子) 的資料表。

當您執行命令時，您應該在 `Close` 命令之後呼叫和 [ReleaseCommand](#releasecommand) 。

當您想要重複執行相同的命令時，您應該在呼叫之前先呼叫來釋放每個結果集存取子 `Close` `Execute` 。 在數列的結尾，您應該呼叫來釋放參數存取子 `ReleaseCommand` 。 另一個常見的案例是呼叫具有 output 參數的預存程式。 在許多提供者 (（例如 SQL Server 的 OLE DB 提供者）) 將無法存取輸出參數值，除非您關閉結果集存取子。 呼叫 `Close` 以關閉傳回的資料列集和結果集存取子，但不是參數存取子，因此可讓您取得輸出參數值。

### <a name="example"></a>範例

下列範例示範如何在您重複執行相同的命令時，呼叫 `Close` 和 `ReleaseCommand`。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a> CCommand：： GetNextResult

如果有可用的結果集，則提取下一個結果集。

### <a name="syntax"></a>語法

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>參數

*pulRowsAffected*<br/>
[in/out]記憶體的指標，其中會傳回受命令影響的資料列計數。

*bBind*<br/>
在指定是否要在執行之後自動系結命令。 預設值是 **`true`** ，它會自動系結命令。 設定 *bBind* 以 **`false`** 防止命令的自動系結，讓您可以手動進行系結。  (手動系結對 OLAP 使用者特別感興趣。 ) 

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如果之前已提取過結果集，此函式會釋放先前的結果集，並將資料行解除系結。 如果 *bBind* 為 **`true`** ，則會系結新的資料行。

只有在您藉由設定 `CCommand` 範本參數*TMultiple*來指定多個結果時，才應該呼叫此函數 = `CMultipleResults` 。

## <a name="ccommandopen"></a><a name="open"></a> CCommand：： Open

執行並選擇性地系結命令。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>參數

*會話*<br/>
在要在其中執行命令的會話。

*wszCommand*<br/>
在要執行的命令，以 Unicode 字串傳遞。 當使用時，可以是 Null `CAccessor` ，在此情況下，會從傳遞給 [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) 宏的值中取出命令。 如需詳細資料，請參閱*OLE DB 程式設計人員參考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

*szCommand*<br/>
在與 *wszCommand* 相同，不同之處在于此參數會採用 ANSI 命令字串。 這個方法的第四個形式可以採用 Null 值。 如需詳細資訊，請參閱本主題稍後的「備註」。

*pPropSet*<br/>
在 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 結構陣列的指標，其中包含要設定的屬性和值。 請參閱 Windows SDK 中的 OLE DB 程式設計*人員參考*中的[屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*pRowsAffected*<br/>
[in/out]記憶體的指標，其中會傳回受命令影響的資料列計數。 如果* \* PROWSAFFECTED*為 Null，則不會傳回任何資料列計數。 否則，會 `Open` 根據下列條件設定* \* pRowsAffected* ：

|如果|結果為|
|--------|----------|
|的 `cParamSets` 元素 `pParams` 大於1|* \* pRowsAffected*代表在執行中指定的所有參數集影響的資料列總數。|
|無法使用受影響的資料列數目|* \* pRowsAffected*設定為-1。|
|此命令不會更新、刪除或插入資料列|未定義* \* pRowsAffected* 。|

*guidCommand*<br/>
在GUID，指定提供者在剖析命令文字時要使用的語法和一般規則。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))和[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) 。

*bBind*<br/>
在指定是否要在執行之後自動系結命令。 預設值是 **`true`** ，它會自動系結命令。 設定 *bBind* 以 **`false`** 防止命令的自動系結，讓您可以手動進行系結。  (手動系結對 OLAP 使用者特別感興趣。 ) 

*ulPropSets*<br/>
在在*pPropSet*引數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數目。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

前三種形式的 `Open` 會取得會話、建立命令，並視需要系結任何參數，然後執行命令。

的第一種形式 `Open` 是採用 Unicode 命令字串，而且沒有預設值。

的第二種形式是 `Open` 採用 ANSI 命令字串，而且沒有預設值 (提供給現有的 ANSI 應用程式) 回溯相容性。

的第三種形式 `Open` 允許命令字串是 null，因為的型別 **`int`** 預設值為 null。 它會提供給呼叫 `Open(session, NULL);` 或， `Open(session);` 因為 Null 的型別為 **`int`** 。 此版本需要和判斷提示 **`int`** 參數為 Null。

`Open`當您已建立命令，而且想要執行單一[準備](#prepare)和多個執行時，請使用第四種形式的。

> [!NOTE]
> `Open` 呼叫 `Execute` ，然後再呼叫 `GetNextResult` 。

## <a name="ccommandcreate"></a><a name="create"></a> CCommand：： Create

呼叫 [CCommand：： CreateCommand](#createcommand) 來建立指定之會話的命令，然後呼叫 [ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 來指定命令文字。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>參數

*會話*<br/>
在要在其上建立命令的會話。

*wszCommand*<br/>
在命令字串的 Unicode 文字指標。

*szCommand*<br/>
在命令字串的 ANSI 文字指標。

*guidCommand*<br/>
在GUID，指定提供者在剖析命令文字時要使用的語法和一般規則。 如需方言的說明，請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

的第一種形式 `Create` 是採用 Unicode 命令字串。 的第二種形式 `Create` 會採用 ANSI 命令字串 (提供給現有的 ansi 應用程式) 與舊版相容。

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a> CCommand：： CreateCommand

建立新的命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>參數

*會話*<br/>
在 `CSession` 要與新命令相關聯的物件。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用指定的會話物件來建立命令。

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a> CCommand：： GetParameterInfo

取得命令參數、其名稱及其類型的清單。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandWithParameters：： GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="ccommandprepare"></a><a name="prepare"></a> CCommand：:P 準備

驗證並優化目前的命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>參數

*cExpectedRuns*<br/>
在您預期要執行命令的次數。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會包裝 OLE DB 方法 [ICommandPrepare：:P 準備](/previous-versions/windows/desktop/ms718370(v=vs.85))。

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a> CCommand：： ReleaseCommand

釋放參數存取子，然後再釋放命令本身。

### <a name="syntax"></a>語法

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>備註

`ReleaseCommand` 與一起使用 `Close` 。 請參閱 [關閉](#close) 以取得使用量詳細資料。

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a> CCommand：： SetParameterInfo

指定每個命令參數的原生類型。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandWithParameters：： SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="ccommandunprepare"></a><a name="unprepare"></a> CCommand：： Unprepare

捨棄目前的命令執行計畫。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會包裝 OLE DB 方法 [ICommandPrepare：： Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

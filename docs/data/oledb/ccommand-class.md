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
ms.openlocfilehash: 73b02f0ffb9d9b98a17933cc3b17c8627121e3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228917"
---
# <a name="ccommand-class"></a>CCommand 類別

提供設定和執行命令的方法。

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
`CDynamicParameterAccessor` `CDynamicStringAccessor` `CEnumeratorAccessor` 您想要讓命令使用之存取子類別的類型（例如、或）。 預設值為 `CNoAccessor` ，它會指定類別不支援參數或輸出資料行。

*TRowset*<br/>
`CArrayRowset` `CNoRowset` 您想要讓命令使用的資料列集類別類型（例如或）。 預設為 `CRowset`。

*TMultiple*<br/>
若要使用可傳回多個結果的 OLE DB 命令，請指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否則，請使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 如需詳細資訊，請參閱[IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85))。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[關閉](#close)|關閉目前的命令。|
|[GetNextResult](#getnextresult)|使用多個結果集時，提取下一個結果。|
|[開啟](#open)|執行，並選擇性地系結命令。|

### <a name="inherited-methods"></a>繼承的方法

|||
|-|-|
|[建立](#create)|為指定的會話建立新的命令，然後設定命令文字。|
|[CreateCommand](#createcommand)|建立新的命令。|
|[GetParameterInfo](#getparameterinfo)|取得命令參數的清單、其名稱和類型。|
|[準備](#prepare)|驗證並優化目前的命令。|
|[ReleaseCommand](#releasecommand)|視需要釋放參數存取子，然後釋放命令。|
|[SetParameterInfo](#setparameterinfo)|指定每個命令參數的原生類型。|
|[Unprepare](#unprepare)|捨棄目前的命令執行計畫。|

## <a name="remarks"></a>備註

當您需要執行以參數為基礎的作業或執行命令時，請使用這個類別。 如果您只需要開啟簡單的資料列集，請改用[CTable](../../data/oledb/ctable-class.md) 。

您所使用的存取子類別會決定系結參數和資料的方法。

請注意，您無法使用預存程式搭配 OLE DB Provider for Jet，因為該提供者不支援預存程式（查詢字串中只允許常數）。

## <a name="ccommandclose"></a><a name="close"></a>CCommand：： Close

釋放與命令相關聯的存取子資料列集。

### <a name="syntax"></a>語法

```cpp
void Close();
```

### <a name="remarks"></a>備註

命令會使用資料列集、結果集存取子和（選擇性）參數存取子（不同于不支援參數但不需要參數存取子的資料表）。

當您執行命令時，您應該在 `Close` 命令後面呼叫和[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) 。

當您想要重複執行相同的命令時，您應該在呼叫之前呼叫，以釋放每個結果集存取子 `Close` `Execute` 。 在數列的結尾，您應該呼叫來釋放參數存取子 `ReleaseCommand` 。 另一個常見的案例是呼叫具有輸出參數的預存程式。 在許多提供者（例如 SQL Server 的 OLE DB 提供者）中，輸出參數值將無法存取，直到您關閉結果集存取子為止。 呼叫 `Close` 以關閉傳回的資料列集和結果集存取子，但不是參數存取子，因此可讓您取得輸出參數值。

### <a name="example"></a>範例

下列範例示範如何在您重複執行相同的命令時，呼叫 `Close` 和 `ReleaseCommand`。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand：： GetNextResult

提取下一個結果集（如果有的話）。

### <a name="syntax"></a>語法

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>參數

*pulRowsAffected*<br/>
[in/out]傳回受命令影響的資料列計數之記憶體的指標。

*bBind*<br/>
在指定是否要在執行後自動系結命令。 預設值為 **`true`** ，這會自動系結命令。 將*bBind*設定為可 **`false`** 防止自動系結命令，讓您可以手動系結。 （對 OLAP 使用者而言，手動系結特別重要）。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如果先前已提取結果集，此函式會釋放先前的結果集，並將資料行解除系結。 如果*bBind*為 **`true`** ，則會系結新的資料行。

只有在您已藉由設定 `CCommand` 範本參數*TMultiple*來指定多個結果時，才應該呼叫此函式 = `CMultipleResults` 。

## <a name="ccommandopen"></a><a name="open"></a>CCommand：： Open

執行，並選擇性地系結命令。

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

*本次*<br/>
在要在其中執行命令的會話。

*wszCommand*<br/>
在要執行的命令，傳遞為 Unicode 字串。 當使用時，可以是 Null `CAccessor` ，在此情況下，會從傳遞至[DEFINE_COMMAND](../../data/oledb/define-command.md)宏的值抓取命令。 如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ICommand：： Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) 。

*szCommand*<br/>
在與*wszCommand*相同，不同之處在于此參數會接受 ANSI 命令字串。 此方法的第四種形式可以接受 Null 值。 如需詳細資訊，請參閱本主題稍後的「備註」。

*pPropSet*<br/>
在[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構陣列的指標，其中包含要設定的屬性和值。 請參閱 Windows SDK 中 OLE DB 程式設計*人員參考*中的[屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*pRowsAffected*<br/>
[in/out]傳回受命令影響的資料列計數之記憶體的指標。 如果* \* PROWSAFFECTED*為 Null，則不會傳回任何資料列計數。 否則，會 `Open` 根據下列條件設定* \* pRowsAffected* ：

|If|結果為|
|--------|----------|
|的 `cParamSets` 元素 `pParams` 大於1|* \* pRowsAffected*代表在執行中指定的所有參數集所影響的資料列總數。|
|受影響的資料列數目無法使用|* \* pRowsAffected*設定為-1。|
|此命令不會更新、刪除或插入資料列|未定義* \* pRowsAffected* 。|

*guidCommand*<br/>
在GUID，指定要在剖析命令文字時使用之提供者的語法和一般規則。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))和[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) 。

*bBind*<br/>
在指定是否要在執行後自動系結命令。 預設值為 **`true`** ，這會自動系結命令。 將*bBind*設定為可 **`false`** 防止自動系結命令，讓您可以手動系結。 （對 OLAP 使用者而言，手動系結特別重要）。

*ulPropSets*<br/>
在在*傳入 ppropset*引數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數目。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

前三種形式的 `Open` 會採用會話、建立命令，並執行命令，並視需要系結任何參數。

第一種形式的 `Open` 會採用 Unicode 命令字串，而且沒有預設值。

的第二種形式 `Open` 採用 ANSI 命令字串，而且沒有預設值（提供給現有 ANSI 應用程式的回溯相容性）。

第三種形式的可 `Open` 讓命令字串成為 null，因為類型的 **`int`** 預設值為 null。 它是為了呼叫或而提供， `Open(session, NULL);` `Open(session);` 因為 Null 的類型為 **`int`** 。 此版本需要，並判斷提示 **`int`** 參數為 Null。

`Open`當您已經建立命令，而您想要執行單一[準備](../../data/oledb/ccommand-prepare.md)和多個執行時，請使用第四種形式的。

> [!NOTE]
> `Open`呼叫 `Execute` ，然後再呼叫 `GetNextResult` 。

## <a name="ccommandcreate"></a><a name="create"></a>CCommand：： Create

呼叫[CCommand：： CreateCommand](../../data/oledb/ccommand-createcommand.md)以建立指定會話的命令，然後呼叫[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))來指定命令文字。

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

*本次*<br/>
在要在其上建立命令的會話。

*wszCommand*<br/>
在命令字串之 Unicode 文字的指標。

*szCommand*<br/>
在命令字串的 ANSI 文字指標。

*guidCommand*<br/>
在GUID，指定要在剖析命令文字時使用之提供者的語法和一般規則。 如需方言的說明，請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

第一種形式 `Create` 採用 Unicode 命令字串。 的第二種形式 `Create` 採用 ANSI 命令字串（提供給與現有 ansi 應用程式的回溯相容性）。

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand：： CreateCommand

建立新的命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>參數

*本次*<br/>
在`CSession`要與新命令相關聯的物件。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會使用指定的會話物件來建立命令。

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand：： GetParameterInfo

取得命令參數的清單、其名稱和類型。

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

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand：:P 準備

驗證並優化目前的命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>參數

*cExpectedRuns*<br/>
在您預期會執行命令的次數。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會包裝 OLE DB 方法[ICommandPrepare：:P 準備](/previous-versions/windows/desktop/ms718370(v=vs.85))。

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand：： ReleaseCommand

釋放參數存取子，然後再釋放命令本身。

### <a name="syntax"></a>語法

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>備註

`ReleaseCommand`與搭配使用 `Close` 。 請參閱[關閉](../../data/oledb/ccommand-close.md)以取得使用方式詳細資料。

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand：： SetParameterInfo

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

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand：： Unprepare

捨棄目前的命令執行計畫。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

這個方法會包裝 OLE DB 方法[ICommandPrepare：： Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

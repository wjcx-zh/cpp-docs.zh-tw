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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368622"
---
# <a name="ccommand-class"></a>CCommand 類別

提供設置和執行命令的方法。

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
您希望命令使用的存取器類別(如`CDynamicParameterAccessor``CDynamicStringAccessor`、`CEnumeratorAccessor`或 )。 預設值為`CNoAccessor`,它指定類不支援參數或輸出列。

*特羅塞特*<br/>
希望命令使用的行集類的類型(如`CArrayRowset``CNoRowset`或)。 預設值為 `CRowset`。

*T 倍數*<br/>
要使用可以傳回多個結果的 OLE DB 指令,請指定[CMulti 結果](../../data/oledb/cmultipleresults-class.md)。 否則,請使用[CNoMulti 結果](../../data/oledb/cnomultipleresults-class.md)。 有關詳細資訊,請參閱[I 倍數結果](/previous-versions/windows/desktop/ms721289(v=vs.85))。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[關閉](#close)|關閉當前命令。|
|[取得下一個結果](#getnextresult)|使用多個結果集時獲取下一個結果。|
|[開啟](#open)|執行並選擇性地綁定命令。|

### <a name="inherited-methods"></a>繼承的方法

|||
|-|-|
|[建立](#create)|為指定的作業階段建立新命令,然後設置命令文本。|
|[CreateCommand](#createcommand)|建立新命令。|
|[取得參數資訊](#getparameterinfo)|取得命令的參數、名稱及其類型的清單。|
|[準備](#prepare)|驗證並優化當前命令。|
|[發佈命令](#releasecommand)|如有必要,釋放參數訪問器,然後釋放命令。|
|[設定參數資訊](#setparameterinfo)|指定每個指令參數的本機類型。|
|[未準備](#unprepare)|放棄當前命令執行計劃。|

## <a name="remarks"></a>備註

當您需要執行基於參數的操作或執行命令時,請使用此類。 如果只需要打開一個簡單的行集,請使用[CTable。](../../data/oledb/ctable-class.md)

您使用的存取器類確定綁定參數和資料的方法。

請注意,您不能將儲存過程與 Jet 的 OLE DB 提供程式一起使用,因為該提供者不支援儲存過程(查詢字串中只允許常量)。

## <a name="ccommandclose"></a><a name="close"></a>指令:關閉

釋放與命令關聯的訪問器行集。

### <a name="syntax"></a>語法

```cpp
void Close();
```

### <a name="remarks"></a>備註

命令使用行集、結果集訪問器和(可選)參數訪問器(與不支援參數並且不需要參數訪問器的表不同)。

執行命令時,應在命令之後調用兩`Close`個命令和[「釋放命令](../../data/oledb/ccommand-releasecommand.md)」。。

如果要重複執行同一命令,則應在調用`Close``Execute`之前調用 釋放每個結果集訪問器。 在序列的末尾,應通過調用`ReleaseCommand`釋放參數訪問器。 另一個常見方案是調用具有輸出參數的存儲過程。 在許多提供程式(如 SQL Server 的 OLE DB 提供程式)上,在關閉結果集訪問器之前,將無法訪問輸出參數值。 呼叫`Close`以關閉傳回的行集和結果集存取器,但不關閉參數訪問器,從而允許您檢索輸出參數值。

### <a name="example"></a>範例

下列範例示範如何在您重複執行相同的命令時，呼叫 `Close` 和 `ReleaseCommand`。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>指令::取得下一個結果

如果結果集可用,則提取下一個結果集。

### <a name="syntax"></a>語法

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>參數

*脈衝影響*<br/>
[進出]指向返回受命令影響的行計數的記憶體的指標。

*bBind*<br/>
[在]指定在執行後是否自動綁定命令。 預設值為**true**,這將導致命令自動綁定。 將*bBind*設置為**false**會阻止命令的自動綁定,以便您可以手動綁定。 (OLAP 用戶特別感興趣的手動綁定。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如果以前已提取結果集,則此函數將釋放上一個結果集並取消綁定列。 如果*bBind* **為 true,** 則綁定新列。

僅當通過設置範本參數*TMulti*=`CMultipleResults`,指定了多個`CCommand`結果時 ,才應調用此函數。

## <a name="ccommandopen"></a><a name="open"></a>指令::開啟

執行並選擇性地綁定命令。

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

*工作階段*<br/>
[在]要在其中執行命令的會話。

*wszCommand*<br/>
[在]要執行的命令,作為 Unicode 字串傳遞。 使用`CAccessor`時可以為 NULL,在這種情況下,將從傳遞給[DEFINE_COMMAND](../../data/oledb/define-command.md)宏的值中檢索該命令。 有關詳細資訊,請參閱[ICommand::在](/previous-versions/windows/desktop/ms718095(v=vs.85)) *OLE DB 程式師參考中*執行。

*szCommand*<br/>
[在]與*wszCommand*相同,只不過此參數採用 ANSI 命令字串。 此方法的第四種形式可以採用 NULL 值。 有關詳細資訊,請參閱本主題後面的"備註"。

*pPropSet*<br/>
[在]指向包含要設置的屬性和值的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構陣列的指標。 請參考 Windows SDK 中的*OLE DB 程式者參考*中[屬性集與屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*pRows 受影響的*<br/>
[進出]指向返回受命令影響的行計數的記憶體的指標。 如果*\*PRows 受影響的*為 NULL,則不返回任何行計數。 否則,`Open`根據以下條件設定*\*pRows 受影響的*:

|If|結果為|
|--------|----------|
|`cParamSets``pParams`元素大於 1|pRows受影響的表示受執行中指定的所有參數集影響的行總數。 * \* *|
|受影響的行數無法用|pRows 受影響的設置為 -1。 * \* *|
|這個指令不更新、刪除或插入列|pRows 受影響的未定義*\**。|

*吉德命令*<br/>
[在]指定提供者用於分析命令文本的語法和一般規則的 GUID。 有關詳細資訊[,請參閱 ICommandText:取得命令文本](/previous-versions/windows/desktop/ms709825(v=vs.85))和[ICommandText:在](/previous-versions/windows/desktop/ms709757(v=vs.85)) *OLE DB 程式師參考*中設定命令文本。

*bBind*<br/>
[在]指定在執行後是否自動綁定命令。 預設值為**true**,這將導致命令自動綁定。 將*bBind*設置為**false**會阻止命令的自動綁定,以便您可以手動綁定。 (OLAP 用戶特別感興趣的手動綁定。

*ulPropSets*<br/>
[在]*在 pPropSet*參數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

前三種形式採取`Open`工作階段、創建命令和執行命令,根據需要綁定任何參數。

第一種形式`Open`採用 Unicode 命令字串,並且沒有預設值。

第二種形式`Open`採用 ANSI 命令字串,沒有預設值(針對與現有 ANSI 應用程式的向後相容性提供)。

第三種形式`Open`允許命令字串為 NULL,因為類型**int**的預設值為 NULL。 它用於呼叫`Open(session, NULL);``Open(session);`或 因為 NULL 的類型**int**。此版本要求並斷言**int**參數為 NULL。

使用第四種形式,`Open`當您已經建立命令,並且想要執行單個[準備](../../data/oledb/ccommand-prepare.md)和多次執行時。

> [!NOTE]
> `Open`呼叫`Execute`,這反過來呼`GetNextResult`叫 。

## <a name="ccommandcreate"></a><a name="create"></a>指令::建立

呼叫[CCommand::建立指令](../../data/oledb/ccommand-createcommand.md)為指定的作業階段建立命令,然後呼叫[ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))指定命令文字。

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

*工作階段*<br/>
[在]要在其上創建命令的工作階段。

*wszCommand*<br/>
[在]指向命令字串的 Unicode 文字的指標。

*szCommand*<br/>
[在]指向命令字串的 ANSI 文字的指標。

*吉德命令*<br/>
[在]指定提供者用於分析命令文本的語法和一般規則的 GUID。 有關方言的說明,請參閱[ICommandText:在](/previous-versions/windows/desktop/ms709825(v=vs.85)) *OLE DB 程式師參考*中獲取命令文本。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

的第一種形式`Create`採用 Unicode 命令字串。 第二種形式`Create`採用 ANSI 命令字串(針對與現有 ANSI 應用程式的向後相容性提供)。

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>指令::建立命令

建立新命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>參數

*工作階段*<br/>
[在]要`CSession`與新命令關聯的物件。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此方法使用指定的作業物件創建命令。

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>指令:抓取參數資訊

取得命令的參數、名稱及其類型的清單。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>參數

請參考[ICommand 與參數:取得 OLE](/previous-versions/windows/desktop/ms714917(v=vs.85)) *DB 程式者參考*中的參數資訊 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="ccommandprepare"></a><a name="prepare"></a>C命令::P雷帕雷雷

驗證並優化當前命令。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>參數

*c預期執行*<br/>
[在]預期執行命令的次數。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此方法包裝 OLE DB 方法[ICommandPrepare::P重新資料](/previous-versions/windows/desktop/ms718370(v=vs.85))。

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>命令:釋放命令

釋放參數存取子，然後再釋放命令本身。

### <a name="syntax"></a>語法

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>備註

`ReleaseCommand`與結合使用`Close`。 有關使用方式的詳細資訊,請參閱[關閉](../../data/oledb/ccommand-close.md)。

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>指令::設定參數資訊

指定每個指令參數的本機類型。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>參數

請參考[ICommand 與參數::在](/previous-versions/windows/desktop/ms725393(v=vs.85))OLE *DB 程式者參考*中設定參數資訊 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="ccommandunprepare"></a><a name="unprepare"></a>命令::未準備

放棄當前命令執行計劃。

### <a name="syntax"></a>語法

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此方法包裝 OLE DB 方法[ICommandPrepare:::取消準備](/previous-versions/windows/desktop/ms719635(v=vs.85))。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

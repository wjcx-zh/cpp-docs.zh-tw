---
title: CSession 類別
ms.date: 11/04/2016
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: 72797411b100480a06e27b71b000264070e57e32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211129"
---
# <a name="csession-class"></a>CSession 類別

表示單一資料庫存取會話。

## <a name="syntax"></a>語法

```cpp
class CSession
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[Abort](#abort)|取消（終止）交易。|
|[關閉](#close)|關閉會話。|
|[認可](#commit)|認可交易。|
|[GetTransactionInfo](#gettransactioninfo)|傳回交易的相關資訊。|
|[開啟](#open)|為數據源物件開啟新的會話。|
|[StartTransaction](#starttransaction)|開始此會話的新交易。|

## <a name="remarks"></a>備註

一或多個會話可以與每個提供者連接（資料來源）相關聯，其以[CDataSource](../../data/oledb/cdatasource-class.md)物件表示。 若要建立 `CDataSource`的新 `CSession`，請呼叫[CSession：： Open](../../data/oledb/csession-open.md)。 若要開始資料庫交易，`CSession` 提供 `StartTransaction` 方法。 一旦交易啟動之後，您可以使用 `Commit` 方法進行認可，或使用 `Abort` 方法將它取消。

## <a name="csessionabort"></a><a name="abort"></a>CSession：： Abort

終止交易。

### <a name="syntax"></a>語法

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ITransaction：： Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="csessionclose"></a><a name="close"></a>CSession：： Close

關閉由[CSession：： Open](../../data/oledb/csession-open.md)開啟的會話。

### <a name="syntax"></a>語法

```cpp
void Close() throw();
```

### <a name="remarks"></a>備註

釋放 `m_spOpenRowset` 指標。

## <a name="csessioncommit"></a><a name="commit"></a>CSession：： Commit

認可交易。

### <a name="syntax"></a>語法

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ITransaction：： Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[ITransaction：： Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))。

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a>CSession：： GetTransactionInfo

傳回交易的相關資訊。

### <a name="syntax"></a>語法

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ITransaction：： GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[ITransaction：： GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) 。

## <a name="csessionopen"></a><a name="open"></a>CSession：： Open

為數據源物件開啟新的會話。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>參數

*ds*<br/>
在要開啟會話的資料來源。

*傳入 ppropset*<br/>
在[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構陣列的指標，其中包含要設定的屬性和值。 請參閱 Windows SDK 中 OLE DB 程式設計*人員參考*中的[屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*ulPropSets*<br/>
在在*傳入 ppropset*引數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數目。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

您必須先使用[CDataSource：： open](../../data/oledb/cdatasource-open.md)開啟資料來源物件，然後再將它傳遞給 `CSession::Open`。

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a>CSession：： StartTransaction

開始此會話的新交易。

### <a name="syntax"></a>語法

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ITransactionLocal：： StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[ITransactionLocal：： StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

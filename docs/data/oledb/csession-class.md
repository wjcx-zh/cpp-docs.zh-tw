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
ms.openlocfilehash: 6858c26df5f5ee364717d089704117e650282278
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841099"
---
# <a name="csession-class"></a>CSession 類別

表示單一資料庫存取會話。

## <a name="syntax"></a>語法

```cpp
class CSession
```

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[中止](#abort)|取消 (終止) 交易。|
|[關閉](#close)|關閉會話。|
|[認可](#commit)|認可交易。|
|[GetTransactionInfo](#gettransactioninfo)|傳回有關交易的資訊。|
|[開啟](#open)|開啟資料來源物件的新會話。|
|[StartTransaction](#starttransaction)|開始此會話的新交易。|

## <a name="remarks"></a>備註

一或多個會話可以與每個提供者連接 (資料來源) （由 [CDataSource](../../data/oledb/cdatasource-class.md) 物件表示）相關聯。 若要建立的新 `CSession` `CDataSource` ，請呼叫 [CSession：： Open](../../data/oledb/csession-open.md)。 若要開始資料庫交易，請 `CSession` 提供 `StartTransaction` 方法。 一旦啟動交易，您可以使用方法來認可它 `Commit` ，或使用方法來取消交易 `Abort` 。

## <a name="csessionabort"></a><a name="abort"></a> CSession：： Abort

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

## <a name="csessionclose"></a><a name="close"></a> CSession：： Close

關閉會話（由 [CSession：： Open](../../data/oledb/csession-open.md)開啟）。

### <a name="syntax"></a>語法

```cpp
void Close() throw();
```

### <a name="remarks"></a>備註

釋放 `m_spOpenRowset` 指標。

## <a name="csessioncommit"></a><a name="commit"></a> CSession：： Commit

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

如需詳細資訊，請參閱 [ITransaction：： Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))。

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a> CSession：： GetTransactionInfo

傳回有關交易的資訊。

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

## <a name="csessionopen"></a><a name="open"></a> CSession：： Open

開啟資料來源物件的新會話。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>參數

*Ds*<br/>
在要開啟會話的資料來源。

*pPropSet*<br/>
在 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 結構陣列的指標，其中包含要設定的屬性和值。 請參閱 Windows SDK 中的 OLE DB 程式設計*人員參考*中的[屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*ulPropSets*<br/>
在在*pPropSet*引數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數目。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

您必須先使用 [CDataSource：： open](../../data/oledb/cdatasource-open.md) 開啟資料來源物件，再將它傳遞至 `CSession::Open` 。

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a> CSession：： StartTransaction

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
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

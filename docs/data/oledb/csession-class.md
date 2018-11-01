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
ms.openlocfilehash: 317e24708a6f4e5666c59c0db870440895173d7c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550315"
---
# <a name="csession-class"></a>CSession 類別

表示單一的資料庫存取工作階段。

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
|[Abort](#abort)|取消 （終止） 交易。|
|[關閉](#close)|關閉工作階段。|
|[認可](#commit)|認可的交易。|
|[GetTransactionInfo](#gettransactioninfo)|傳回交易的相關資訊。|
|[開啟](#open)|開啟資料來源物件的新工作階段。|
|[StartTransaction](#starttransaction)|開始新的交易，此工作階段。|

## <a name="remarks"></a>備註

一或多個工作階段可由每個提供者連接 （資料來源），與相關聯[CDataSource](../../data/oledb/cdatasource-class.md)物件。 若要建立新`CSession`for `CDataSource`，呼叫[csession:: Open](../../data/oledb/csession-open.md)。 若要開始資料庫交易`CSession`提供`StartTransaction`方法。 交易啟動之後，您可以在使用認可`Commit`方法，或取消使用`Abort`方法。

## <a name="abort"></a> Csession:: Abort

結束交易。

### <a name="syntax"></a>語法

```cpp
HRESULT Abort(BOID* pboidReason = NULL, 
   BOOL bRetaining = FALSE, 
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>參數

請參閱[itransaction:: Abort](/previous-versions/windows/desktop/ms709833)中*OLE DB 程式設計人員參考*。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

## <a name="close"></a> Csession:: Close

關閉工作階段，利用已開啟[csession:: Open](../../data/oledb/csession-open.md)。

### <a name="syntax"></a>語法

```cpp
void Close() throw();
```

### <a name="remarks"></a>備註

版本`m_spOpenRowset`指標。

## <a name="commit"></a> Csession:: Commit

認可的交易。

### <a name="syntax"></a>語法

```cpp
HRESULT Commit(BOOL bRetaining = FALSE, 
   DWORD grfTC = XACTTC_SYNC, 
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>參數

請參閱[itransaction:: Commit](/previous-versions/windows/desktop/ms713008)中*OLE DB 程式設計人員參考*。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [itransaction:: Commit](/previous-versions/windows/desktop/ms713008)。

## <a name="gettransactioninfo"></a> Csession:: Gettransactioninfo

傳回交易的相關資訊。

### <a name="syntax"></a>語法

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>參數

請參閱[ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975)中*OLE DB 程式設計人員參考*。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975)中*OLE DB 程式設計人員參考*。

## <a name="open"></a> Csession:: Open

開啟資料來源物件的新工作階段。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>參數

*ds*<br/>
[in]若要開啟工作階段的資料來源。

*pPropSet*<br/>
[in]陣列的指標[DBPROPSET](/previous-versions/windows/desktop/ms714367)結構，其中包含要設定屬性和值。 請參閱[的屬性集和屬性群組](/previous-versions/windows/desktop/ms713696)中*OLE DB 程式設計人員參考*Windows SDK 中。

*ulPropSets*<br/>
[in]數目[DBPROPSET](/previous-versions/windows/desktop/ms714367)結構傳入*Dbpropset*引數。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

您必須開啟資料來源物件使用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)再傳遞給`CSession::Open`。

## <a name="starttransaction"></a> Csession:: Starttransaction

開始新的交易，此工作階段。

### <a name="syntax"></a>語法

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>參數

請參閱[itransactionlocal:: Starttransaction](/previous-versions/windows/desktop/ms709786)中*OLE DB 程式設計人員參考*。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [itransactionlocal:: Starttransaction](/previous-versions/windows/desktop/ms709786)中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[CatDB](../../visual-cpp-samples.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
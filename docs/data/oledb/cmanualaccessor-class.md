---
title: CManualAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 4d9fb79bbf5203fa959672faec8c3b076c17f1ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211844"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 類別

表示專為先進使用而設計的存取子類型。

## <a name="syntax"></a>語法

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddBindEntry](#addbindentry)|將繫結項目加入至輸出資料行。|
|[AddParameterEntry](#addparameterentry)|將參數專案加入至參數存取子。|
|[CreateAccessor](#createaccessor)|配置資料行系結結構的記憶體，並初始化資料行資料成員。|
|[CreateParameterAccessor](#createparameteraccessor)|配置參數系結結構的記憶體，並初始化參數資料成員。|

## <a name="remarks"></a>備註

使用 `CManualAccessor`，您可以透過執行時間函式呼叫來指定參數和輸出資料行系結。

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a>CManualAccessor：： AddBindEntry

將繫結項目加入至輸出資料行。

### <a name="syntax"></a>語法

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
在資料行編號。

*wType*<br/>
在資料類型。

*nColumnSize*<br/>
在資料行大小（以位元組為單位）。

*pData*<br/>
在緩衝區中儲存之資料行資料的指標。

*pLength*<br/>
在欄位長度的指標（如有需要）。

*pStatus*<br/>
在要系結至資料行狀態之變數的指標（如有需要）。

### <a name="remarks"></a>備註

若要使用此函數，您必須先呼叫[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。 您無法新增超過 `CreateAccessor`中指定之資料行數目的專案。

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a>CManualAccessor：： AddParameterEntry

將參數專案加入至參數專案結構。

### <a name="syntax"></a>語法

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
在參數編號。

*wType*<br/>
在資料類型。

*nColumnSize*<br/>
在資料行大小（以位元組為單位）。

*pData*<br/>
在緩衝區中儲存之資料行資料的指標。

*pLength*<br/>
在欄位長度的指標（如有需要）。

*pStatus*<br/>
在要系結至資料行狀態之變數的指標（如有需要）。

*eParamIO*<br/>
在指定與系結相關聯的參數是否為輸入、輸入/輸出或輸出參數。

### <a name="remarks"></a>備註

若要使用此函數，您必須先呼叫[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a>CManualAccessor：： CreateAccessor

配置資料行系結結構的記憶體，並初始化資料行資料成員。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>參數

*nBindEntries*<br/>
在資料行數目。 這個數位應符合[CManualAccessor：： AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)函式的呼叫次數。

*pBuffer*<br/>
在儲存輸出資料行之緩衝區的指標。

*nBufferSize*<br/>
在緩衝區的大小（以位元組為單位）。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

呼叫 `CManualAccessor::AddBindEntry` 函式之前，請先呼叫此函式。

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a>CManualAccessor：： CreateParameterAccessor

配置參數系結結構的記憶體，並初始化參數資料成員。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>參數

*nBindEntries*<br/>
在資料行數目。

*pBuffer*<br/>
在儲存輸入資料行之緩衝區的指標。

*nBufferSize*<br/>
在緩衝區的大小（以位元組為單位）。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

呼叫[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)之前，您必須先呼叫此函式。

## <a name="see-also"></a>另請參閱

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)

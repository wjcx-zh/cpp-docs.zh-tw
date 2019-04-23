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
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
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
ms.openlocfilehash: 526415f14172911b26462fab97d9e0a7513b8cad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027606"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 類別

代表設計供進階使用存取子類型。

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
|[AddBindEntry](#addbindentry)|將輸出資料行的繫結項目。|
|[AddParameterEntry](#addparameterentry)|將參數存取子中參數項目。|
|[CreateAccessor](#createaccessor)|資料行繫結結構配置記憶體，並初始化資料行的資料成員。|
|[CreateParameterAccessor](#createparameteraccessor)|參數繫結結構配置記憶體，初始化參數的資料成員。|

## <a name="remarks"></a>備註

使用`CManualAccessor`，您可以指定參數和輸出資料行繫結的執行階段函式呼叫。

## <a name="addbindentry"></a> Cmanualaccessor:: Addbindentry

將輸出資料行的繫結項目。

### <a name="syntax"></a>語法

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in]資料行編號。

*wType*<br/>
[in]資料型別。

*nColumnSize*<br/>
[in]資料行大小 （位元組）。

*pData*<br/>
[in]儲存在緩衝區資料行的資料指標。

*pLength*<br/>
[in]如有必要的欄位長度指標。

*pStatus*<br/>
[in]如有需要繫結至資料行狀態中，變數的指標。

### <a name="remarks"></a>備註

若要使用此函式，您必須先呼叫[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。 您無法新增更多的項目中指定的資料行數目比`CreateAccessor`。

## <a name="addparameterentry"></a> Cmanualaccessor:: Addparameterentry

將參數項目加入至參數項目結構。

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

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in]參數編號。

*wType*<br/>
[in]資料型別。

*nColumnSize*<br/>
[in]資料行大小 （位元組）。

*pData*<br/>
[in]儲存在緩衝區資料行的資料指標。

*pLength*<br/>
[in]如有必要的欄位長度指標。

*pStatus*<br/>
[in]如有需要繫結至資料行狀態中，變數的指標。

*eParamIO*<br/>
[in]指定與繫結相關聯的參數是否為輸入、 輸入/輸出或輸出參數。

### <a name="remarks"></a>備註

若要使用此函式，您必須先呼叫[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。

## <a name="createaccessor"></a> CManualAccessor::CreateAccessor

資料行繫結結構配置記憶體，並初始化資料行的資料成員。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>參數

*nBindEntries*<br/>
[in]資料行數目。 此數目應符合的呼叫次數[cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)函式。

*pBuffer*<br/>
[in]儲存的輸出資料行緩衝區的指標。

*nBufferSize*<br/>
[in]以位元組為單位的緩衝區大小。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

呼叫此函式，然後再呼叫`CManualAccessor::AddBindEntry`函式。

## <a name="createparameteraccessor"></a> CManualAccessor::CreateParameterAccessor

參數繫結結構配置記憶體，初始化參數的資料成員。

### <a name="syntax"></a>語法

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>參數

*nBindEntries*<br/>
[in]資料行數目。

*pBuffer*<br/>
[in]儲存的輸入資料行緩衝區的指標。

*nBufferSize*<br/>
[in]以位元組為單位的緩衝區大小。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

您必須呼叫此函式，然後再呼叫[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)。

## <a name="see-also"></a>另請參閱

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)
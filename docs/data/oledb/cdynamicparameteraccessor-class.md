---
title: CDynamicParameterAccessor 類別
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: 9c326c337ff210ef9de26b3fd88c0d853832b260
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211860"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor 類別

類似於 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ，但藉由呼叫 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 介面取得要設定的參數資訊。

## <a name="syntax"></a>語法

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|建構函式。|
|[GetParam](#getparam)|從緩衝區擷取參數資料。|
|[GetParamCount](#getparamcount)|擷取存取子中的參數數目。|
|[GetParamIO](#getparamio)|判斷指定的參數為輸入或輸出參數。|
|[GetParamLength](#getparamlength)|擷取儲存在緩衝區中的指定參數的長度。|
|[GetParamName](#getparamname)|擷取指定的參數名稱。|
|[GetParamStatus](#getparamstatus)|擷取儲存在緩衝區中的指定參數的狀態。|
|[GetParamString](#getparamstring)|擷取儲存在緩衝區中的指定參數的字串資料。|
|[GetParamType](#getparamtype)|擷取指定參數的資料類型。|
|[SetParam](#setparam)|設定使用參數資料的緩衝區。|
|[SetParamLength](#setparamlength)|設定儲存在緩衝區中的指定參數的長度。|
|[SetParamStatus](#setparamstatus)|設定儲存在緩衝區中的指定參數的狀態。|
|[SetParamString](#setparamstring)|設定儲存在緩衝區中的指定參數的字串資料。|

## <a name="remarks"></a>備註

提供者必須支援 `ICommandWithParameters` 讓取用者使用這個類別。

參數資訊會儲存在這個類別建立和管理的緩衝區中。 使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)從緩衝區取得參數資料。

如需示範如何使用這個類別來執行 SQL Server 預存程式並取得輸出參數值的範例，請參閱 GitHub 上[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)存放庫中的[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)範例程式碼。

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a>CDynamicParameterAccessor：： CDynamicParameterAccessor

建構函式。

### <a name="syntax"></a>語法

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>參數

*eBlobHandling*<br/>
指定 BLOB 資料的處理方式。 預設值為 DBBLOBHANDLING_DEFAULT。 如需 DBBLOBHANDLINGENUM 值的說明，請參閱[CDynamicAccessor：： SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) 。

*nBlobSize*<br/>
最大 BLOB 的大小 (以位元組為單位)；此值的資料行資料被視為 BLOB。 預設值為8000。 如需詳細資訊，請參閱[CDynamicAccessor：： SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) 。

### <a name="remarks"></a>備註

如需 BLOB 處理的詳細資訊，請參閱[CDynamicAccessor：： CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md)函數。

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a>CDynamicParameterAccessor：： GetParam

從參數緩衝區抓取指定之參數的非字串資料。

### <a name="syntax"></a>語法

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>參數

*ctype*<br/>
屬於資料類型的樣板化參數。

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pParamName*<br/>
在參數名稱。

*pData*<br/>
脫銷包含從緩衝區抓取之資料的記憶體指標。

### <a name="return-value"></a>傳回值

針對樣板版本，會指向包含從緩衝區取得之資料的記憶體。 針對樣板化版本，會在成功時傳回**true** ，否則會傳回**false** 。

使用 `GetParam` 從緩衝區取出非字串參數資料。 使用[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)從緩衝區取出字串參數資料。

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a>CDynamicParameterAccessor：： GetParamCount

擷取儲存在緩衝區中的參數數目。

### <a name="syntax"></a>語法

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>傳回值

參數的數目。

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a>CDynamicParameterAccessor：： GetParamIO

判斷指定的參數為輸入或輸出參數。

### <a name="syntax"></a>語法

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pParamIO*<br/>
變數的指標，其中包含指定參數的 `DBPARAMIO` 類型（輸入或輸出）。 其定義如下：

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>傳回值

如果成功，則傳回**true** ，否則會傳回**false** 。

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a>CDynamicParameterAccessor：： GetParamLength

擷取儲存在緩衝區中的指定參數的長度。

### <a name="syntax"></a>語法

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pLength*<br/>
[out] 指向變數的指標，該變數含有所指定參數的長度 (以位元組為單位)。

### <a name="remarks"></a>備註

第一個覆寫會在成功時傳回**true** ，否則會傳回**false** 。 第二個覆寫會指向含有參數長度的記憶體。

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a>CDynamicParameterAccessor：： GetParamName

抓取指定之參數的名稱。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

### <a name="return-value"></a>傳回值

指定參數的名稱。

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a>CDynamicParameterAccessor：： GetParamStatus

擷取儲存在緩衝區中的指定參數的狀態。

### <a name="syntax"></a>語法

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pStatus*<br/>
脫銷變數的指標，其中包含指定之參數的 DBSTATUS 狀態。 如需 DBSTATUS 值的詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))，或在 oledb 中搜尋 DBSTATUS。

### <a name="remarks"></a>備註

第一個覆寫會在成功時傳回**true** ，否則會傳回**false** 。 第二個覆寫會指向記憶體，其中包含指定參數的狀態。

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a>CDynamicParameterAccessor：： GetParamString

擷取儲存在緩衝區中的指定參數的字串資料。

### <a name="syntax"></a>語法

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*strOutput*<br/>
脫銷指定之參數的 ANSI （`CSimpleStringA`）或 Unicode （`CSimpleStringW`）字串資料。 您應該傳遞 `CString`類型的參數，例如：

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
脫銷指定參數之 ANSI （**CHAR**）或 Unicode （**WCHAR**）字串資料的指標。

*pMaxLen*<br/>
脫銷*PBuffer*所指向之緩衝區大小的指標（以字元為單位，包括終止的 Null）。

### <a name="remarks"></a>備註

如果成功，則傳回**true** ，否則會傳回**false** 。

如果*pBuffer*為 Null，這個方法會在*pMaxLen*所指向的記憶體中設定所需的緩衝區大小，並傳回**true**而不復制資料。

如果緩衝區*pBuffer*不夠大，無法包含整個字串，這個方法將會失敗。

使用 `GetParamString`，從緩衝區取出字串參數資料。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)從緩衝區取出非字串參數資料。

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a>CDynamicParameterAccessor：： GetParamType

擷取指定參數的資料類型。

### <a name="syntax"></a>語法

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pType*<br/>
脫銷變數的指標，其中包含指定之參數的資料類型。

### <a name="return-value"></a>傳回值

如果成功，則傳回**true** ，否則會傳回**false** 。

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a>CDynamicParameterAccessor：： SetParam

使用指定的（非字串）資料設定參數緩衝區。

### <a name="syntax"></a>語法

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>參數

*ctype*<br/>
屬於資料類型的樣板化參數。

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 例如：

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
在參數名稱。

*pData*<br/>
在包含要寫入緩衝區之資料的記憶體指標。

*status*<br/>
在DBSTATUS 資料行狀態。 如需 DBSTATUS 值的詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))，或在 oledb 中搜尋 DBSTATUS。

### <a name="return-value"></a>傳回值

如果成功，則傳回**true** ，否則會傳回**false** 。

使用 `SetParam` 來設定緩衝區中的非字串參數資料。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)來設定緩衝區中的字串參數資料。

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a>CDynamicParameterAccessor：： SetParamLength

設定儲存在緩衝區中的指定參數的長度。

### <a name="syntax"></a>語法

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*length*<br/>
在指定參數的長度（以位元組為單位）。

### <a name="remarks"></a>備註

如果成功，則傳回**true** ，否則會傳回**false** 。

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a>CDynamicParameterAccessor：： SetParamStatus

設定儲存在緩衝區中的指定參數的狀態。

### <a name="syntax"></a>語法

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*status*<br/>
在指定之參數的 DBSTATUS 狀態。 如需 DBSTATUS 值的詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))，或在 oledb 中搜尋 DBSTATUS。

### <a name="remarks"></a>備註

如果成功，則傳回**true** ，否則會傳回**false** 。

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a>CDynamicParameterAccessor：： SetParamString

設定儲存在緩衝區中的指定參數的字串資料。

### <a name="syntax"></a>語法

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>參數

*nParam*<br/>
[in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 如需範例，請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pString*<br/>
在指定參數之 ANSI （**CHAR**）或 Unicode （**WCHAR**）字串資料的指標。 請參閱 DBSTATUS （在 oledb. h 中）。

*status*<br/>
在指定之參數的 DBSTATUS 狀態。 如需 DBSTATUS 值的詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[狀態](/previous-versions/windows/desktop/ms722617(v=vs.85))，或在 oledb 中搜尋 DBSTATUS。

### <a name="remarks"></a>備註

如果成功，則傳回**true** ，否則會傳回**false** 。

如果您嘗試設定大於*pString*指定之大小上限的字串，`SetParamString` 將會失敗。

使用 `SetParamString` 在緩衝區中設定字串參數資料。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)來設定緩衝區中的非字串參數資料。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)

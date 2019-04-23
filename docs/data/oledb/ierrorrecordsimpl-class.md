---
title: IErrorRecordsImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: b1ab6b0984cbf84690d69a3ffe7eb3931bf59563
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029469"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 類別

實作 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))介面，加入至記錄，以及從資料成員擷取的記錄 ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 的型別**CAtlArray <** `RecordClass`**>**.

## <a name="syntax"></a>語法

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>參數

*T*<br/>
類別衍生自`IErrorRecordsImpl`。

*RecordClass*<br/>
表示 OLE DB 錯誤物件的類別。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|從錯誤記錄中取得錯誤描述字串。|
|[GetErrorGUID](#geterrorguid)|從錯誤記錄中取得錯誤的 GUID。|
|[GetErrorHelpContext](#geterrorhelpcontext)|從錯誤記錄中取得的說明內容識別碼。|
|[GetErrorHelpFile](#geterrorhelpfile)|從錯誤記錄中取得說明檔的完整路徑名稱。|
|[GetErrorSource](#geterrorsource)|取得錯誤來源的程式碼，從錯誤記錄。|

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|您可以將記錄加入 OLE DB 錯誤物件。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|傳回錯誤，例如傳回碼和提供者特定錯誤號碼的相關基本資訊。|
|[GetCustomErrorObject](#getcustomerrorobject)|傳回自訂錯誤物件介面的指標。|
|[GetErrorInfo](#geterrorinfo)|傳回[IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))介面指標上指定的記錄。|
|[GetErrorParameters](#geterrorparameters)|傳回的錯誤參數。|
|[GetRecordCount](#getrecordcount)|OLE DB 記錄物件中傳回記錄的數目。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_rgErrors](#rgerrors)|錯誤記錄的陣列。|

## <a name="geterrordescriptionstring"></a> IErrorRecordsImpl::GetErrorDescriptionString

從錯誤記錄中取得錯誤描述字串。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`記錄`IErrorInfo`介面。

### <a name="return-value"></a>傳回值

描述錯誤的字串指標。

## <a name="geterrorguid"></a> IErrorRecordsImpl::GetErrorGUID

從錯誤記錄中取得錯誤的 GUID。

### <a name="syntax"></a>語法

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`記錄`IErrorInfo`介面。

### <a name="return-value"></a>傳回值

錯誤的 GUID 參考。

## <a name="geterrorhelpcontext"></a> IErrorRecordsImpl::GetErrorHelpContext

從錯誤記錄中取得的說明內容識別碼。

### <a name="syntax"></a>語法

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`記錄`IErrorInfo`介面。

### <a name="return-value"></a>傳回值

錯誤的說明內容識別碼。

## <a name="geterrorhelpfile"></a> IErrorRecordsImpl::GetErrorHelpFile

從錯誤記錄中取得說明檔的路徑名稱。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`記錄`IErrorInfo`介面。

### <a name="return-value"></a>傳回值

包含錯誤的說明檔的路徑名稱的字串指標。

## <a name="geterrorsource"></a> IErrorRecordsImpl::GetErrorSource

取得造成錯誤的錯誤記錄的原始程式碼。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`記錄`IErrorInfo`介面。

### <a name="return-value"></a>傳回值

字串，包含錯誤的原始碼的指標。

## <a name="adderrorrecord"></a> IErrorRecordsImpl::AddErrorRecord

您可以將記錄加入 OLE DB 錯誤物件。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>參數

請參閱[IErrorRecords::AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="getbasicerrorinfo"></a> IErrorRecordsImpl::GetBasicErrorInfo

傳回錯誤，例如傳回碼和提供者特定錯誤號碼的相關基本資訊。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>參數

請參閱[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="getcustomerrorobject"></a> IErrorRecordsImpl::GetCustomErrorObject

傳回自訂錯誤物件介面的指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>參數

請參閱[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="geterrorinfo"></a> IErrorRecordsImpl::GetErrorInfo

傳回[IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))介面指標上指定的記錄。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>參數

請參閱[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="geterrorparameters"></a> Ierrorrecordsimpl:: Geterrorparameters

傳回的錯誤參數。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>參數

請參閱[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="getrecordcount"></a> IErrorRecordsImpl::GetRecordCount

OLE DB 記錄物件中傳回記錄的數目。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>參數

請參閱[IErrorRecords::GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="rgerrors"></a> IErrorRecordsImpl::m_rgErrors

錯誤記錄的陣列。

### <a name="syntax"></a>語法

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
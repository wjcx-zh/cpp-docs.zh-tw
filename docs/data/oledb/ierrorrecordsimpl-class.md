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
ms.openlocfilehash: 189f97e72f1cb87de7e4c4a388128c2a76c42961
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832434"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 類別

執行 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))介面、將記錄加入至資料 (成員的記錄，並從**CAtlArray<** 類型的[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 中取出記錄 `RecordClass` **>** 。

## <a name="syntax"></a>語法

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IErrorRecordsImpl` 。

*RecordClass*<br/>
代表 OLE DB 錯誤物件的類別。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|從錯誤記錄取得錯誤描述字串。|
|[GetErrorGUID](#geterrorguid)|從錯誤記錄取得錯誤 GUID。|
|[GetErrorHelpCoNtext](#geterrorhelpcontext)|從錯誤記錄取得說明內容識別碼。|
|[GetErrorHelpFile](#geterrorhelpfile)|從錯誤記錄取得說明檔的完整路徑名稱。|
|[GetErrorSource](#geterrorsource)|從錯誤記錄取得錯誤原始程式碼。|

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[AddErrorRecord](#adderrorrecord)|將記錄加入至 OLE DB error 物件。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|傳回錯誤的基本資訊，例如傳回碼和提供者特定的錯誤號碼。|
|[GetCustomErrorObject](#getcustomerrorobject)|傳回自訂錯誤物件之介面的指標。|
|[GetErrorInfo](#geterrorinfo)|傳回指定之記錄上的 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 介面指標。|
|[GetErrorParameters](#geterrorparameters)|傳回錯誤參數。|
|[GetRecordCount](#getrecordcount)|傳回 OLE DB 記錄物件中的記錄數目。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_rgErrors](#rgerrors)|錯誤記錄的陣列。|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a> IErrorRecordsImpl：： GetErrorDescriptionString

從錯誤記錄取得錯誤描述字串。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`介面中的記錄 `IErrorInfo` 。

### <a name="return-value"></a>傳回值

描述錯誤之字串的指標。

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a> IErrorRecordsImpl：： GetErrorGUID

從錯誤記錄取得錯誤 GUID。

### <a name="syntax"></a>語法

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`介面中的記錄 `IErrorInfo` 。

### <a name="return-value"></a>傳回值

錯誤 GUID 的參考。

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a> IErrorRecordsImpl：： GetErrorHelpCoNtext

從錯誤記錄取得說明內容識別碼。

### <a name="syntax"></a>語法

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`介面中的記錄 `IErrorInfo` 。

### <a name="return-value"></a>傳回值

錯誤的說明內容識別碼。

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a> IErrorRecordsImpl：： GetErrorHelpFile

從錯誤記錄取得說明檔的路徑名稱。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`介面中的記錄 `IErrorInfo` 。

### <a name="return-value"></a>傳回值

字串的指標，其中包含錯誤說明檔的路徑名稱。

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a> IErrorRecordsImpl：： GetErrorSource

取得造成錯誤記錄錯誤的原始程式碼。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>參數

*rCurError*<br/>
`ERRORINFO`介面中的記錄 `IErrorInfo` 。

### <a name="return-value"></a>傳回值

字串的指標，其中包含錯誤的原始程式碼。

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a> IErrorRecordsImpl：： AddErrorRecord

將記錄加入至 OLE DB error 物件。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) 。

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> IErrorRecordsImpl：： GetBasicErrorInfo

傳回錯誤的基本資訊，例如傳回碼和提供者特定的錯誤號碼。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 。

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a> IErrorRecordsImpl：： GetCustomErrorObject

傳回自訂錯誤物件之介面的指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 。

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a> IErrorRecordsImpl：： GetErrorInfo

傳回指定之記錄上的 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 介面指標。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a> IErrorRecordsImpl：： GetErrorParameters

傳回錯誤參數。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 。

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a> IErrorRecordsImpl：： GetRecordCount

傳回 OLE DB 記錄物件中的記錄數目。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) 。

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a> IErrorRecordsImpl：： m_rgErrors

錯誤記錄的陣列。

### <a name="syntax"></a>語法

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)

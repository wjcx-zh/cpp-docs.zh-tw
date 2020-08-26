---
title: CDBErrorInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: 5c26a3f1e8b5589afebd72c7b722ab9ed9e4229d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838304"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 類別

提供使用 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) 介面 OLE DB 錯誤處理的支援。

## <a name="syntax"></a>語法

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|傳回錯誤記錄中包含的所有錯誤資訊。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|呼叫 [IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) ，以傳回有關指定錯誤的基本資訊。|
|[GetCustomErrorObject](#getcustomerrorobject)|呼叫 [IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) ，將指標傳回至自訂錯誤物件上的介面。|
|[GetErrorInfo](#geterrorinfo)|呼叫 [IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) ，以傳回 `IErrorInfo` 指定之記錄的介面指標。|
|[GetErrorParameters](#geterrorparameters)|呼叫 [IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 傳回錯誤參數。|
|[GetErrorRecords](#geterrorrecords)|取得指定之物件的錯誤記錄。|

## <a name="remarks"></a>備註

此介面會傳回一或多個錯誤記錄給使用者。 先呼叫 [CDBErrorInfo：： GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) ，以取得錯誤記錄的計數。 然後呼叫其中一個存取函式，例如 [CDBErrorInfo：： GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)，以抓取每個記錄的錯誤資訊。

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a> CDBErrorInfo：： GetAllErrorInfo

傳回錯誤記錄中所包含的所有錯誤資訊類型。

### <a name="syntax"></a>語法

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>參數

*ulRecordNum*<br/>
[in] 要傳回錯誤資訊之記錄的以零起始數字。

*lcid*<br/>
[in] 要傳回之錯誤資訊的地區設定 ID。

*pbstrDescription*<br/>
[out] 如果不支援地區設定，則傳回錯誤的文字描述指標或 NULL。 請參閱＜備註＞。

*pbstrSource*<br/>
[out] 包含產生錯誤之元件名稱的字串指標。

*pguid*<br/>
[out] 定義錯誤之介面的 GUID 指標。

*pdwHelpContext*<br/>
[out] 錯誤的說明主題內容識別碼指標。

*pbstrHelpFile*<br/>
[out] 包含描述錯誤說明檔路徑之字串的指標。

### <a name="return-value"></a>傳回值

如果成功，S_OK。 如需其他傳回值的 OLE DB 程式設計*人員參考*，請參閱[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

### <a name="remarks"></a>備註

*PbstrDescription*的輸出值是藉由呼叫在內部取得 `IErrorInfo::GetDescription` ，如果不支援地區設定，或下列兩個條件都成立，則會將值設為 Null：

1. *lcid*的值不是美國英文，

1. *lcid*的值不等於 GetUserDefaultLCID 所傳回的值。

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> CDBErrorInfo：： GetBasicErrorInfo

呼叫 [IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 來傳回有關錯誤的基本資訊，例如傳回碼和提供者特定的錯誤號碼。

### <a name="syntax"></a>語法

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a> CDBErrorInfo：： GetCustomErrorObject

呼叫 [IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) ，將指標傳回至自訂錯誤物件上的介面。

### <a name="syntax"></a>語法

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a> CDBErrorInfo：： GetErrorInfo

呼叫 [IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) ，將 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 介面指標傳回至指定的記錄。

### <a name="syntax"></a>語法

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a> CDBErrorInfo：： GetErrorParameters

呼叫 [IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 傳回錯誤參數。

### <a name="syntax"></a>語法

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IErrorRecords：： GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a> CDBErrorInfo：： GetErrorRecords

取得指定之物件的錯誤記錄。

### <a name="syntax"></a>語法

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>參數

*朋 克*<br/>
在要取得錯誤記錄之物件的介面。

*Iid*<br/>
在與錯誤相關聯之介面的 IID。

*pcRecords*<br/>
擴展指向 (一) 錯誤記錄計數的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如果您想要檢查要從中取得錯誤資訊的介面，請使用第一種形式的函數。 否則，請使用第二個表單。

## <a name="see-also"></a>另請參閱

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)

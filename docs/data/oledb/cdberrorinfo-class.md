---
title: CDBErrorInfo 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd5b08ed22c715a91a1f9fd97749fa6293fa75bb
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084161"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 類別

支援使用 OLE DB 的 OLE DB 錯誤處理[IErrorRecords](/previous-versions/windows/desktop/ms718112)介面。  
  
## <a name="syntax"></a>語法

```cpp
class CDBErrorInfo  
``` 

## <a name="requirements"></a>需求  

**標題:** atldbcli.h 
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetAllErrorInfo](#getallerrorinfo)|傳回包含錯誤記錄中的所有錯誤資訊。|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|呼叫[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)來傳回指定的錯誤相關的基本資訊。|  
|[GetCustomErrorObject](#getcustomerrorobject)|呼叫[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)介面的指標，傳回自訂錯誤物件。|  
|[GetErrorInfo](#geterrorinfo)|呼叫[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)返回`IErrorInfo`介面指標，以指定的記錄。|  
|[GetErrorParameters](#geterrorparameters)|呼叫[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)傳回錯誤的參數。|  
|[GetErrorRecords](#geterrorrecords)|取得指定的物件中的錯誤記錄。|  
  
## <a name="remarks"></a>備註  

這個介面會傳回給使用者的一或多個錯誤記錄。 呼叫[cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)第一個，以取得錯誤記錄的計數。 然後呼叫其中一個存取權，這類函式[cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)，擷取每一筆記錄的資訊時發生錯誤。  
  
## <a name="getallerrorinfo"></a> Cdberrorinfo:: Getallerrorinfo

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

如果成功傳回 S_OK。 請參閱[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)中*OLE DB 程式設計人員參考*其他傳回值。  
  
### <a name="remarks"></a>備註  

輸出值*pbstrDescription*藉由呼叫從內部取得`IErrorInfo::GetDescription`，這將設定的值為 NULL，不支援的地區設定，則這兩個下列條件成立：  
  
1. 值*lcid*不是美國英文和  
  
1. 值*lcid*不是等於 GetUserDefaultLCID 所傳回的值。 

## <a name="getbasicerrorinfo"></a> Cdberrorinfo:: Getbasicerrorinfo

呼叫[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)傳回錯誤，例如傳回碼和提供者特定錯誤號碼的相關基本資訊。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,   
   ERRORINFO* pErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="getcustomerrorobject"></a> Cdberrorinfo:: Getcustomerrorobject

呼叫[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)介面的指標，傳回自訂錯誤物件。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,   
   REFIID riid,IUnknown** ppObject) const throw();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="geterrorinfo"></a> Cdberrorinfo:: Geterrorinfo

呼叫[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)返回[IErrorInfo](/previous-versions/windows/desktop/ms718112)介面指標，以指定的記錄。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,   
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[ierrorrecords:: Geterrorinfo](/previous-versions/windows/desktop/ms711230)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="geterrorparameters"></a> Cdberrorinfo:: Geterrorparameters

呼叫[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)傳回錯誤的參數。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,   
   DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="geterrorrecords"></a> Cdberrorinfo:: Geterrorrecords

取得指定的物件中的錯誤記錄。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  

HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>參數  

*pUnk*<br/>
[in]要取得錯誤記錄物件的介面。  
  
*iid*<br/>
[in]與錯誤相關聯之介面的 IID。  
  
*pcRecords*<br/>
[out]指標 （一個為基礎） 的錯誤記錄計數。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

如果您想要檢查哪些介面，以取得錯誤資訊，請使用函式的第一種形式。 否則，請使用第二種形式。  
  
## <a name="see-also"></a>另請參閱  

[DBViewer](../../visual-cpp-samples.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
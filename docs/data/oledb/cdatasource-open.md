---
title: 'Cdatasource:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3196aa89426e895dd6b73b28ce197e8f271a0262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097064"
---
# <a name="cdatasourceopen"></a>CDataSource::Open
開啟資料來源使用的連接**CLSID**， **ProgID**，或`CEnumerator`moniker 或以定位程式對話方塊提示使用者。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  


HRESULT Open(const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,  
  DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,  
   LPCTSTR pName,  LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(HWND hWnd = GetActiveWindow(),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,   
  DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,   
   LPCTSTR pName,LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `clsid`  
 [in]**CLSID**的資料提供者。  
  
 *pPropSet*  
 [in]陣列的指標[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構，其中包含要設定屬性和值。 請參閱[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
 *nPropertySets*  
 [in]數目[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構傳入*Dbpropset*引數。  
  
 *pName*  
 [in] 要連接的資料庫名稱。  
  
 *pUserName*  
 [in] 使用者的名稱。  
  
 *pPassword*  
 [in] 使用者的密碼。  
  
 `nInitMode`  
 [in] 資料庫初始化模式。 請參閱[初始化屬性](https://msdn.microsoft.com/en-us/library/ms723127.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中針對一份有效初始化模式。 如果 `nInitMode` 是零，則用來開啟連接的屬性集不包含任何初始化模式。  
  
 `szProgID`  
 [in] 程式識別碼。  
  
 `enumerator`  
 [in]A [CEnumerator](../../data/oledb/cenumerator-class.md)物件，用來取得 moniker，以便開啟連接，當呼叫端未指定**CLSID**。  
  
 `hWnd`  
 [in] 做為對話方塊之父視窗的控制代碼。 如果使用的函式多載用到 `hWnd` 參數，將會自動叫用服務元件。如需詳細資訊，請參閱＜備註＞。  
  
 `dwPromptOptions`  
 [in] 決定要顯示的定位程式對話方塊樣式。 請參閱 Msdasc.h 中的可能值。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如果方法多載使用 `hWnd` 參數，則會使用 oledb32.dll 中的服務元件開啟資料來源物件。此 DLL 包含服務元件功能的實作，例如資源共用、自動交易登記等。 如需詳細資訊，請參閱 < OLE DB 服務 > 中 OLE DB 程式設計人員參考[ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
 如果方法多載未使用 `hWnd` 參數，則會在不使用 oledb32.dll 中的服務元件的情況下開啟資料來源物件。 A [CDataSource](../../data/oledb/cdatasource-class.md)使用這些函式多載開啟的物件將無法利用任何服務元件的功能。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用 OLE DB 範本開啟 Jet 4.0 資料來源。 您可以將 Jet 資料來源當做 OLE DB 資料來源。 不過，您呼叫**開啟**需要兩個屬性集： 一個用於**DBPROPSET_DBINIT**和另一個則用於**DBPROPSET_JETOLEDB_DBINIT**，如此一來，您可以設定**DBPROP_JETOLEDB_DATABASEPASSWORD**。  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)

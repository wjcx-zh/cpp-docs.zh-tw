---
title: 'Cdatasource:: Openfromfilename |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
dev_langs:
- C++
helpviewer_keywords:
- OpenFromFileName method
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6dfa5411373ab4a5c80c493ad876926620c4f9a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopenfromfilename"></a>CDataSource::OpenFromFileName
從以使用者提供的檔名指定的檔案，開啟資料來源。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `szFileName`  
 [in] 檔案的名稱，通常是資料來源連接 (.UDL) 檔案。  
  
 如需詳細資料連結檔 （.udl 檔案） 的詳細資訊，請參閱[資料連結 API 概觀](https://msdn.microsoft.com/en-us/library/ms718102.aspx)Windows SDK 中。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。 如需詳細資訊，請參閱 < OLE DB 服務 > 中 OLE DB 程式設計人員參考[ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)
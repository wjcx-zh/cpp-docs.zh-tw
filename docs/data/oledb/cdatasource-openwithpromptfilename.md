---
title: "Cdatasource:: Openwithpromptfilename |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
dev_langs: C++
helpviewer_keywords: OpenWithPromptFileName method
ms.assetid: 89460504-1aaf-4412-aa7b-fa5a4b39ada3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 272fd65eb0fda3a087853ca3a5793618d356fc7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopenwithpromptfilename"></a>CDataSource::OpenWithPromptFileName
此方法會以對話方塊提示使用者，然後使用使用者所指定的檔案開啟資料來源。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT OpenWithPromptFileName(   
   HWND hWnd = GetActiveWindow(   
   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `hWnd`  
 [in] 做為對話方塊之父視窗的控制代碼。  
  
 `dwPromptOptions`  
 [in] 決定要顯示的定位程式對話方塊樣式。 請參閱 Msdasc.h 中的可能值。  
  
 *szInitialDirectory*  
 [in] 要顯示在定位器對話方塊中的初始目錄。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。 如需詳細資訊，請參閱 < OLE DB 服務 > 中 OLE DB 程式設計人員參考[http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)
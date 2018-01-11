---
title: "Cdatasource:: Openfrominitializationstring |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs: C++
helpviewer_keywords: OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 294c5cd893b04dd477a002adb6dc03fa33c60a29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
開啟資料來源的使用者提供初始化字串所指定。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *szInitializationString*  
 [in]初始化字串。  
  
 *fPromptForInfo*  
 [in]如果這個引數設定為**true**，然後`OpenFromInitializationString`將設定**DBPROP_INIT_PROMPT**屬性**DBPROMPT_COMPLETEREQUIRED**，使用者是指定只有當您需要更多的資訊提示。 這非常有用的情況下初始化字串中指定的資料庫，需要密碼，但字串不包含密碼。 密碼 （或任何其他遺失的資訊），將提示使用者嘗試連接至資料庫時。  
  
 預設值是**false**，永遠不會提示使用者指定 (設定**DBPROP_INIT_PROMPT**至**DBPROMPT_NOPROMPT**)。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會使用 oledb32.dll 中的服務元件開啟資料來源物件；此 DLL 包含服務元件功能的實作，例如資源集中化、自動交易登記等。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)
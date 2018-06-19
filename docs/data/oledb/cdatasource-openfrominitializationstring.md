---
title: 'Cdatasource:: Openfrominitializationstring |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs:
- C++
helpviewer_keywords:
- OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dac964f7c6c863f85769a164fab8c418e1c45430
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090930"
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
開啟資料來源的使用者提供初始化字串所指定。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
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
  
## <a name="see-also"></a>另請參閱  
 [CDataSource 類別](../../data/oledb/cdatasource-class.md)
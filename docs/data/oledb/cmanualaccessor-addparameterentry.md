---
title: 'Cmanualaccessor:: Addparameterentry |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
dev_langs:
- C++
helpviewer_keywords:
- AddParameterEntry method
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb97e841cf72abcf49ee2a57ccd78832e7fb95a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessoraddparameterentry"></a>CManualAccessor::AddParameterEntry
將參數項目加入至參數項目結構。  
  
## <a name="syntax"></a>語法  
  
```
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程式設計人員參考*。  
  
 `nOrdinal`  
 [in]參數數目。  
  
 `wType`  
 [in]資料型別。  
  
 `nColumnSize`  
 [in]資料行大小 （位元組）。  
  
 `pData`  
 [in]儲存在緩衝區資料行的資料指標。  
  
 `pLength`  
 [in]必要的欄位長度指標。  
  
 `pStatus`  
 [in]如果需要繫結至資料行狀態中，變數的指標。  
  
 *eParamIO*  
 [in]指定與繫結相關聯的參數是否為輸入、 輸入/輸出或輸出參數。  
  
## <a name="remarks"></a>備註  
 若要使用此函式，您必須先呼叫[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [Cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [DBViewer 範例](../../visual-cpp-samples.md)
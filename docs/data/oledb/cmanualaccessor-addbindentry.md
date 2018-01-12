---
title: "Cmanualaccessor:: Addbindentry |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs: C++
helpviewer_keywords: AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14a2fbae8ee29728d145b3ff8d20a02b4000b5a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
將繫結項目加入至輸出資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void AddBindEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL   
) throw ( );  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程式設計人員參考*。  
  
 `nOrdinal`  
 [in]資料行編號。  
  
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
  
## <a name="remarks"></a>備註  
 若要使用此函式，您必須先呼叫[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。 您無法加入更多的項目中指定的資料行數目比`CreateAccessor`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 範例](../../visual-cpp-samples.md)
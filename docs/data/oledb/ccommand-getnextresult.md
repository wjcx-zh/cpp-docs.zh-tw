---
title: 'Ccommand:: Getnextresult |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs:
- C++
helpviewer_keywords:
- GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d833c3e644ac6ed44216542ce4fc6d995cc22efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
提取下一個結果集，如果有的話。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,  
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *pulRowsAffected*  
 [輸入/輸出]其中會傳回命令影響的資料列計數的記憶體指標。  
  
 `bBind`  
 [in]指定是否要自動繫結的命令之後執行。 預設值是**true**，因而導致命令會自動繫結。 設定`bBind`至**false**可防止自動繫結的命令，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者的特別感興趣的）。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如果先前擷取的結果集，此函式會釋放前一個結果集和資料行解除繫結。 如果`bBind`是**true**，它會繫結的新資料行。  
  
 只有當您藉由設定指定多個結果，應該呼叫此函式`CCommand`樣板參數*TMultiple*=`CMultipleResults`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)
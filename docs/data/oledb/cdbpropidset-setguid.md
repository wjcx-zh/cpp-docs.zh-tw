---
title: 'Cdbpropidset:: Setguid |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87878b6cc7ae38f2c9ffcf597a56ab020d8e9c8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090321"
---
# <a name="cdbpropidsetsetguid"></a>CDBPropIDSet::SetGUID
設定中的 GUID 欄位**DBPROPIDSET**結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 [in]若要設定使用 GUID **guidPropertySet**欄位[DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx)結構。  
  
## <a name="remarks"></a>備註  
 這個欄位可以設定[建構函式](../../data/oledb/cdbpropidset-cdbpropidset.md)以及。 如果您為這個類別使用預設建構函式，則呼叫此函式。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDBPropIDSet 類別](../../data/oledb/cdbpropidset-class.md)
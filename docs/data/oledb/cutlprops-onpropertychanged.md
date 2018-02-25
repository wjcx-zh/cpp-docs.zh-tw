---
title: "Cutlprops:: Onpropertychanged |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs:
- C++
helpviewer_keywords:
- OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f87f6842f33bd58be9cde515396f495402235a77
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
設定屬性，以處理鏈結的內容之後呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
      virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>參數  
 `iCurSet`  
 屬性集陣列; 中的索引零，如果只有一個屬性集。  
  
 `pDBProp`  
 內容識別碼和新值[DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)結構。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。 預設會傳回值為`S_OK`。  
  
## <a name="remarks"></a>備註  
 如果您想要處理鏈結的屬性，例如書籤或更新其值會相依於另一個屬性的值，您應該覆寫這個函式。  
  
## <a name="example"></a>範例  
 在這個函式，使用者取得的屬性識別碼`DBPROP*`參數。 現在，很可能比較針對要鏈結的內容識別碼。 當找到屬性時，`SetProperties`稱為現在會搭配其他內容設定的屬性。 在此情況下，如果其中一個取得`DBPROP_IRowsetLocate`， `DBPROP_LITERALBOOKMARKS`，或`DBPROP_ORDEREDBOOKMARKS`屬性，其中一個可以設定`DBPROP_BOOKMARKS`屬性。  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)
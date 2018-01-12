---
title: "Crowset:: Insert |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs: C++
helpviewer_keywords: Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75dfe26fa04f8e639b3d391a9dc703a9a98c70c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetinsert"></a>CRowset::Insert
建立並初始化新的資料列，使用存取子中的資料。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT Insert(   
   int nAccessor = 0,   
   bool bGetHRow = false    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nAccessor`  
 [in]用於插入資料的存取子數目。  
  
 *bGetHRow*  
 [in]指出是否要擷取之插入的資料列的控制代碼。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetChange`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetChange**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
 如果一或多個資料行不是可寫入，插入可能會失敗。 請修改您的資料指標對應以修正這個問題。  
  
## <a name="example"></a>範例  
 下列範例會示範如何透過資料列集來存取資料來源，然後再插入的字串使用資料表中該資料列集。  
  
 首先，建立資料表類別藉由將您的專案中插入新的 ATL 物件。 例如，以滑鼠右鍵按一下工作區 窗格中的專案，然後選取**新 ATL 物件**。 從**資料存取**類別目錄中，選取**消費者**。 建立取用者物件的型別**資料表**。 (選取**資料表**直接從資料表中建立資料列集; 選取**命令**建立的資料列集，透過 SQL 命令。)選取資料來源，指定資料表，以存取該資料來源。 如果您呼叫取用者物件**CCustomerTable**，接下來您將實作您插入的程式碼，如下所示：  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)
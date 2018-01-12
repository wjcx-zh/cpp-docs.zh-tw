---
title: "Cdataconnection:: Operator CSession&amp; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
dev_langs: C++
helpviewer_keywords:
- operator CSession&
- CSession& operator
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 35e28b96c3daddcdf8a9ea4bdf06f9b1410463f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdataconnectionoperator-csessionamp"></a>Cdataconnection:: Operator CSession&amp;
將參考傳回給包含`CSession`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
operator const CSession&();  
  
```  
  
## <a name="remarks"></a>備註  
 這個運算子會傳回至包含參照`CSession`物件，讓您傳遞`CDataConnection`物件其中`CSession`需要參考。  
  
## <a name="example"></a>範例  
 如果您有函式 (例如`func`下方) 會採用`CSession`參考，您可以使用**CSession （& s)**傳遞`CDataConnection`改為物件。  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession*](../../data/oledb/cdataconnection-operator-csession-star.md)
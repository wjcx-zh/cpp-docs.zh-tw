---
title: CDataConnection::operator CDataSource&amp; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs:
- C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c52610d947d60fa7ea1be9b764fd09ae0e777a3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>CDataConnection::operator CDataSource&amp;
將參考傳回給包含`CDataSource`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
operator const CDataSource&() throw();  
  
```  
  
## <a name="remarks"></a>備註  
 這個運算子會傳回至包含參照`CDataSource`物件，讓您傳遞`CDataConnection`物件其中`CDataSource`需要參考。  
  
## <a name="example"></a>範例  
 如果您有函式 (例如`func`下方) 會採用`CDataSource`參考，您可以使用**CDataSource （& s)**傳遞`CDataConnection`改為物件。  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)
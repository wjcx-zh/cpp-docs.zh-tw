---
title: 'Cdataconnection:: Operator CSession * |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs:
- C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97219418f18220cde84c80cb9052f17552a3a45d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
將指標傳回至包含的 `CSession` 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
operator const CSession*() throw();  
  
```  
  
## <a name="remarks"></a>備註  
 這個運算子會將指標傳回至包含的 `CSession` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CSession` 物件。  
  
## <a name="example"></a>範例  
 請參閱[運算子 Csession& （& s)](../../data/oledb/cdataconnection-operator-csession-amp.md)如需使用範例。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)
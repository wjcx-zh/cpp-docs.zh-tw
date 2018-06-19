---
title: 'Cdataconnection:: Operator CDataSource * |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs:
- C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bade9d813fb9804ae353f7c5139f063f278da225
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095335"
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
將指標傳回至包含的 `CDataSource` 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
operator const CDataSource*() throw();  
  
```  
  
## <a name="remarks"></a>備註  
 這個運算子會將指標傳回至包含的 `CDataSource` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CDataSource` 物件。  
  
 請參閱[CDataSource 運算子 （& s)](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)如需使用範例。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)
---
title: CDataConnection::operator CDataSource* | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60eba58d4a3884b191afdca1da0934453a303d8c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)
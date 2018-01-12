---
title: "Cdataconnection:: Operator CSession * |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs: C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 53efb82e9f78b4ea5a76b4f200012ed98fb513d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
將指標傳回至包含的 `CSession` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
operator const CSession*() throw( );  
  
```  
  
## <a name="remarks"></a>備註  
 這個運算子會將指標傳回至包含的 `CSession` 物件，讓您傳遞需要 `CDataConnection` 指標的 `CSession` 物件。  
  
## <a name="example"></a>範例  
 請參閱[運算子 Csession& （& s)](../../data/oledb/cdataconnection-operator-csession-amp.md)如需使用範例。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)
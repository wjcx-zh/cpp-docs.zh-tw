---
title: "Cdataconnection:: Operator bool (OLE DB) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07302c63301a0dd57c68ce12062fb54973980099
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionoperator-bool-ole-db"></a>CDataConnection::operator bool (OLE DB)
判斷目前的工作階段是否為開啟。  
  
## <a name="syntax"></a>語法  
  
```cpp
operator bool() throw();  
  
```  
  
## <a name="remarks"></a>備註  
 傳回`bool`（c + + 資料類型） 值。 **true**表示目前的工作階段已開啟。**false**表示目前的工作階段已關閉。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)
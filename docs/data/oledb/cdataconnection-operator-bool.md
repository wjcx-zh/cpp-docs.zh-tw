---
title: "Cdataconnection:: Operator BOOL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs: C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9a9cfd88e2c1ce141da2a4b345a926cdb412a2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-bool"></a>CDataConnection::operator BOOL
判斷目前的工作階段是否為開啟。  
  
## <a name="syntax"></a>語法  
  
```  
  
operator BOOL( ) throw( );  
  
```  
  
## <a name="remarks"></a>備註  
 傳回**BOOL** (MFC typedef) 值。 **TRUE**表示目前的工作階段已開啟。**FALSE**表示目前的工作階段已關閉。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [Cdataconnection:: Operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)
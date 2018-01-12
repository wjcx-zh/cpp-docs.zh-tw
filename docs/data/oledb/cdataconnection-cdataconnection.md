---
title: "Cdataconnection:: Cdataconnection |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs: C++
helpviewer_keywords: CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fd2deb3978ef3c01d5d70297599be54aabb90cb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
執行個體化並初始化`CDataConnection`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      CDataConnection();   
CDataConnection(  
   const CDataConnection &ds  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ds`  
 [in]參考現有的資料連接。  
  
## <a name="remarks"></a>備註  
 建立新的第一個覆寫`CDataConnection`物件以預設設定。  
  
 建立新的第二個覆寫`CDataConnection`設定等於所指定的資料連線物件的物件。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)
---
title: 'Cdataconnection:: Cdataconnection |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 267341f88886f3ff94a6b828034e8acbaa2dc0c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093320"
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
執行個體化並初始化`CDataConnection`物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>參數  
 `ds`  
 [in]參考現有的資料連接。  
  
## <a name="remarks"></a>備註  
 建立新的第一個覆寫`CDataConnection`物件以預設設定。  
  
 建立新的第二個覆寫`CDataConnection`設定等於所指定的資料連線物件的物件。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)
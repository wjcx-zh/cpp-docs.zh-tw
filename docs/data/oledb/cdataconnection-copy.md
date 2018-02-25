---
title: CDataConnection::Copy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method
ms.assetid: a3dbd70d-36be-49e0-a527-00e3910a7a56
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 043874f9c6047317b29156c957ce99d263dfeca2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectioncopy"></a>CDataConnection::Copy
建立現有的資料連接的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp
      CDataConnection& Copy(const CDataConnection & ds) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `ds`  
 [in]若要複製現有的資料連接的參考。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)
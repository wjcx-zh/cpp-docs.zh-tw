---
title: 'Cdataconnection:: Open |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 2c6f0c01-4954-43ba-973e-861ac8e82892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8be130a1270f3782f7f7c47aab4dfb02101a3a3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionopen"></a>CDataConnection::Open
開啟使用初始化字串的資料來源的連接。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(LPCOLESTR szInitString) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *szInitString*  
 [in]資料來源初始化字串。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)
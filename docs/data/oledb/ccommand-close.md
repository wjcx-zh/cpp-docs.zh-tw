---
title: "Ccommand:: Close |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cad9d6a892b31d4e0c3945d94c36466d72fb9c81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandclose"></a>CCommand::Close
釋放與命令相關聯的存取子資料列集。  
  
## <a name="syntax"></a>語法  
  
```  
void Close( );  
```  
  
## <a name="remarks"></a>備註  
 命令會使用資料列集，結果的 set 存取子，以及 （選擇性） （不同於資料表，這些資料表不支援參數，而且不需要是參數存取子） 的參數存取子。  
  
 當您執行命令時，您應該呼叫兩者`Close`和[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)之後的命令。  
  
 當您想要重複執行相同的命令時，您應該藉由呼叫釋放每個結果的 set 存取子`Close`之前先呼叫`Execute`。 在數列的結尾，您應該釋放參數存取子，藉由呼叫`ReleaseCommand`。 另一個常見案例呼叫具有輸出參數的預存程序。 許多提供者 （例如 SQL Server 的 OLE DB 提供者） 上的輸出參數值將無法存取您必須先關閉結果的 set 存取子。 呼叫`Close`關閉傳回的資料列集和結果的 set 存取子，但不是參數存取子，因此可讓您擷取輸出參數值。  
  
## <a name="example"></a>範例  
 下列範例會示範如何呼叫`Close`和`ReleaseCommand`當您重複執行相同的命令。  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)
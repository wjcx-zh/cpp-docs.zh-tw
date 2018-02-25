---
title: "命令物件介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a26004edcd4b1e32bb7dd960ce927786296ef44b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="command-object-interfaces"></a>命令物件介面
命令物件會使用`IAccessor`介面以指定參數繫結。 取用者可以呼叫`IAccessor::CreateAccessor`，它會將陣列傳遞`DBBINDING`結構。 `DBBINDING` 包含有關 （例如類型和長度） 的資料行繫結資訊。 提供者會接收此結構，並判斷應該傳送之資料的方式，以及是否需要轉換。  
  
 `ICommandText`介面會提供方法來指定文字命令。 `ICommandProperties`介面會處理所有的命令屬性。  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
---
title: "異動物件介面 |Microsoft 文件"
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
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d295bd73fbc8bb5fba7ae443b8a99705768753bf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="transaction-object-interfaces"></a>異動物件介面
交易物件上的資料來源定義不可部分完成的工作單位，並判斷這些工作單位如何彼此相關。 此物件不直接支援 OLE DB 提供者樣板 （也就是說，您必須建立自己的物件）。  
  
 下表顯示 OLE DB 為交易物件所定義的強制與選用介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|強制|否|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|強制|否|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|否|  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
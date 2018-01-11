---
title: "工作階段物件介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: abb869becff4f2a4af9d489736c21b66674cc112
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="session-object-interfaces"></a>工作階段物件介面
下表顯示 OLE DB 所定義的工作階段物件的必要和選擇性介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|強制|[是]|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|強制|[是]|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|強制|[是]|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Optional|否|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Optional|否|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Optional|否|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Optional|否|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Optional|[是]|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Optional|[是]|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Optional|否|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|[是]|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Optional|否|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Optional|否|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Optional|否|  
|[Itransaction::](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Optional|否|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Optional|否|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Optional|否|  
|[J](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Optional|否|  
  
 工作階段物件建立資料列集物件。 如果提供者支援的命令，在工作階段也會建立命令物件 (`CCommand`，實作 OLE DB **TCommand**)。 命令物件會實作`ICommand`介面並使用`ICommand::Execute`資料列集上執行命令，如下圖所示的方法。  
  
 ![提供者概念圖](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
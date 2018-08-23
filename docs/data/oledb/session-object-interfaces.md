---
title: 工作階段物件介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8208a372989fac5fa7c7b0c13b83eb27a4d1444b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572925"
---
# <a name="session-object-interfaces"></a>工作階段物件介面
下表顯示由 OLE DB 定義的工作階段物件的必要和選用的介面。  
  
|介面|是否為必要項？|實作 OLE DB 範本嗎？|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](/previous-versions/windows/desktop/ms709721\(v=vs.85\))|強制|[是]|  
|[IOpenRowset](/previous-versions/windows/desktop/ms716946\(v=vs.85\))|強制|[是]|  
|[ISessionProperties](/previous-versions/windows/desktop/ms713721\(v=vs.85\))|強制|[是]|  
|[IAlterIndex](/previous-versions/windows/desktop/ms714943\(v=vs.85\))|Optional|否|  
|[IAlterTable](/previous-versions/windows/desktop/ms719764\(v=vs.85\))|Optional|否|  
|[IBindResource](/previous-versions/windows/desktop/ms714936\(v=vs.85\))|Optional|否|  
|[ICreateRow](/previous-versions/windows/desktop/ms716832\(v=vs.85\))|Optional|否|  
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\))|Optional|[是]|  
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))|Optional|[是]|  
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593\(v=vs.85\))|Optional|否|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Optional|[是]|  
|[ITableCreation](/previous-versions/windows/desktop/ms713639\(v=vs.85\))|Optional|否|  
|[ITableDefinition](/previous-versions/windows/desktop/ms714277\(v=vs.85\))|Optional|否|  
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947\(v=vs.85\))|Optional|否|  
|[ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Optional|否|  
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071\(v=vs.85\))|Optional|否|  
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893\(v=vs.85\))|Optional|否|  
|[ITransactionObject](/previous-versions/windows/desktop/ms713659\(v=vs.85\))|Optional|否|  
  
 工作階段物件建立資料列集物件。 如果提供者支援的命令，在工作階段也會建立命令物件 (`CCommand`，實作 OLE DB `TCommand`)。 命令物件會實作`ICommand`介面並使用`ICommand::Execute`方法，以在資料列集上執行命令，如下圖所示。  
  
 ![提供者概念圖](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
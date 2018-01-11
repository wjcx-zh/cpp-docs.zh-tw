---
title: "將資料提供者不支援轉換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 438d75ad3a36c82c4f9389d4c9b65d677603f6c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="converting-data-not-supported-by-the-provider"></a>轉換提供者不支援的資料
當取用者要求提供者不支援的資料類型時，OLE DB 提供者範本的程式碼`IRowsetImpl::GetData`呼叫 Msdadc.dll 来轉換的資料類型。  
  
 如果您實作的介面，例如`IRowsetChange`需要資料轉換，您可以呼叫 Msdaenum.dll 來執行轉換。 使用`GetData`為 atldb，做為範例中定義。  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
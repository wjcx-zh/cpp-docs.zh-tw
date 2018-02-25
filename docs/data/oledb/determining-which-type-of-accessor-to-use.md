---
title: "決定要使用之存取子類型 |Microsoft 文件"
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
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28173b18e1f2ab6e7c916679d5fa5a27c08caaeb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="determining-which-type-of-accessor-to-use"></a>決定使用哪一種存取子
在編譯時期或執行階段，您可以判斷資料列集的資料類型。  
  
 如果您需要在編譯時期決定資料類型，使用靜態存取子 (例如`CAccessor`)。 您可以手動方式或使用 ATL OLE DB 消費者精靈來判斷資料類型。  
  
 如果您需要在執行階段決定的資料類型，是使用動態 (`CDynamicAccessor`或其子系) 或手動存取子 (`CManualAccessor`)。 在這些情況下，您可以呼叫`GetColumnInfo`上的資料列集傳回資料行繫結資訊，您可以從中判斷型別。  
  
 下表列出取用者範本中所提供的存取子的類型。 每個存取子都有優點和缺點。 根據您的情況，一個存取子類型應能滿足您的需求。  
  
|存取子類別|繫結|參數|註解|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|建立使用者資料錄與`COLUMN_ENTRY`巨集。 巨集繫結至資料成員中該記錄的存取子。 建立資料列集時，無法解除繫結資料行。|是，透過使用**PARAM_MAP**巨集項目。 一旦完成繫結參數不可以是未繫結。|最快速存取子，因為少量的程式碼。|  
|`CDynamicAccessor`|自動的。|否。|如果您不知道的資料列集中的資料型別很有用。|  
|`CDynamicParameterAccessor`|自動執行的但可以是[覆寫](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，如果提供者支援`ICommandWithParameters`。 自動繫結參數。|低於`CDynamicAccessor`但適用於一般的預存程序的呼叫。|  
|**CDynamicStringAccessor[A,W]**|自動的。|否。|擷取從資料存放區做為字串資料存取的資料。|  
|`CManualAccessor`|手動使用`AddBindEntry`。|使用手動`AddParameterEntry`。|速度非常快。參數和資料行繫結一次。 您決定要使用資料的類型。 (請參閱[DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)範例的範例。)需要更多的程式碼比`CDynamicAccessor`或`CAccessor`。 它則更像直接呼叫 OLE DB。|  
|`CXMLAccessor`|自動的。|否。|擷取從資料存放區做為字串資料存取的資料，並將它格式化為 XML 標記的資料。|  
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)
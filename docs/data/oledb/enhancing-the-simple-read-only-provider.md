---
title: "增強簡單唯讀提供者 |Microsoft 文件"
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
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6eb3c583d217e421909236c09ccac6c406cf6a7c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="enhancing-the-simple-read-only-provider"></a>增強簡單唯讀提供者
本節說明如何增強[簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)在上一節中建立。 `IRowsetLocateImpl` 建立實作`IRowsetLocate`介面，並加入您的書籤支援。  
  
 當您有運作的提供者時，您可以增強，使更新提供者、 處理交易，或增強的資料列擷取演算法的效能。 大部分的提供者增強功能包括將介面加入至現有的 COM 物件。  
  
 下列主題中的範例，以增強的資料列擷取機制加入`IRowsetLocate`介面`CAgentRowset`。 本主題說明如何以：  
  
-   [請 RMyProviderRowset 的繼承自 IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)。  
  
-   [動態決定傳回給取用者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>請參閱  
 [建立簡單唯讀提供者](../../data/oledb/creating-a-simple-read-only-provider.md)
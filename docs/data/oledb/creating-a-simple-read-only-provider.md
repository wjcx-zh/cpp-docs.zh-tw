---
title: "建立簡單唯讀提供者 |Microsoft 文件"
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
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 830ba99037607f4fc8ceac9bad451381c30c7786
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="creating-a-simple-read-only-provider"></a>建立簡單唯讀提供者
當您已建立的 OLE DB 提供者使用 ATL 專案精靈 和 ATL OLE DB 提供者精靈時，您可以新增您想要支援其他功能。 開始檢查的取用者，以及在哪些情況下傳送的資料類型來設計您的提供者。 它是特別重要，判斷是否需要支援的命令、 交易和其他選擇性的物件。 良好的設計 design up front 可加速實作和測試。  
  
 此範例顯示在兩個部分：  
  
-   第一個部分示範如何[建立簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)讀取一組字串。  
  
-   第二個組件顯示如何[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)加`IRowsetLocate`介面。  
  
## <a name="see-also"></a>請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)
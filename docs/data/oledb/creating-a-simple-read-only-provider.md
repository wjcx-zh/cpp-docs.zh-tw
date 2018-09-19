---
title: 建立簡單唯讀提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9f951fba45b23b7e4dde92fc11f2faabb53bd43d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101562"
---
# <a name="creating-a-simple-read-only-provider"></a>建立簡單唯讀提供者

當您建立使用 ATL 專案精靈 和 ATL OLE DB 提供者精靈 的 OLE DB 提供者時，您可以新增您想要支援其他功能。 開始設計您的提供者藉由檢查的取用者，以及在哪些情況下傳送的資料類型。 它是特別重要，以判斷是否需要支援的命令、 交易和其他選用的物件。 事先良好的設計可加速實作和測試。  
  
此範例是以兩個部分所示：  
  
- 第一個部分示範如何[建立簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)讀取一組字串。  
  
- 第二個部分顯示如何[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)藉由新增`IRowsetLocate`介面。  
  
## <a name="see-also"></a>另請參閱  

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)
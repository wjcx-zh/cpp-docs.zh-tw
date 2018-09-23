---
title: 實作連接點精靈 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.cp.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f3c92fa219c32ca00050597dab5adfcec17e86b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703543"
---
# <a name="implement-connection-point-wizard"></a>實作連接點精靈

這個精靈會實作 COM 物件的連接點。 可連接物件 (也就是來源) 可以為本身的介面或任何輸出介面公開連接點。 Visual C++ 和 Windows 都提供具有輸出介面的型別程式庫。 每個輸出介面都可以由物件上的用戶端 (也就是接收，sink) 所實作。  
  
如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。  
  
- **可用的型別程式庫**

   顯示可用的型別程式庫，其中包含介面定義，您可以為其實作連接點。 按一下省略符號按鈕找出包含要使用之型別程式庫的檔案。  
  
- **位置**

   顯示 [可用的型別程式庫] 清單中目前選取之型別程式庫的位置。  
  
- **介面**

   顯示其定義包含在 [可用的型別程式庫] 方塊中目前選取之型別程式庫中的介面。  
  
   |傳輸按鈕|描述|  
   |---------------------|-----------------|  
   |**>**|將 [介面] 清單中目前選取的介面名稱新增至 [實作連接點] 清單。|  
   |**>>**|將 [介面] 清單中所有可用介面名稱新增至 [實作連接點] 清單。|  
   |**\<**|移除 [實作連接點] 清單中目前選取的介面名稱。|  
   |**\<\<**|移除 [實作連接點] 清單中目前列出的所有介面名稱。|  
  
- **實作連接點**

   當您按一下 [完成] 時，顯示您實作其連接點的介面名稱。  
  
## <a name="see-also"></a>請參閱  
 [實作連接點](../ide/implementing-a-connection-point-visual-cpp.md)
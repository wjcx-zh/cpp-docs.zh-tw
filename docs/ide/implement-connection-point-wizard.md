---
title: "實作連接點精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.impl.cp.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f29b4f25d937c2f538373ff85819f7315150e712
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implement-connection-point-wizard"></a>實作連接點精靈
此精靈會實作 COM 物件的連接點。 可連接物件 （也就是來源） 可以公開本身的介面或任何輸出介面的連接點。 Visual c + + 和 Windows 都提供輸出介面的型別程式庫。 每個輸出介面可以實作的物件 （也就是接收） 上的用戶端。  
  
 如需詳細資訊，請參閱[ATL 連接點](../atl/atl-connection-points.md)。  
  
 **可用的型別程式庫**  
 顯示可用的型別程式庫，其中包含介面定義，您可以實作連接點。 按一下省略符號按鈕找出包含要使用的類型程式庫的檔案。  
  
 **位置**  
 顯示的類型程式庫中目前選取位置**可用的型別程式庫**清單。  
  
 **介面**  
 顯示的介面的定義包含類型程式庫中目前選取**可用的型別程式庫**方塊。  
  
|傳送按鈕|描述|  
|---------------------|-----------------|  
|**>**|將加入至**實作連接點**中目前選取的介面名稱**介面**清單。|  
|**>>**|將加入至**實作連接點**清單中可用的所有介面名稱**介面**都清單。|  
|**<**|移除在目前選取的介面名稱**實作連接點**清單。|  
|**<<**|移除所有介面目前所列的名稱**實作連接點**清單。|  
  
 **實作連接點**  
 會顯示的介面的實作連接點當您按一下名稱**完成**。  
  
## <a name="see-also"></a>請參閱  
 [實作連接點](../ide/implementing-a-connection-point-visual-cpp.md)
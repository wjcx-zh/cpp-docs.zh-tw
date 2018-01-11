---
title: "偵錯您的提供者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cfcb90daaf23a5fd8e248d43b920340e38d8057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-your-provider"></a>偵錯提供者
有兩種方式可以偵錯您的提供者：  
  
-   因為提供者會建立程序中，您可以建立某些通常使用的 OLE DB 消費者樣板和逐步執行提供者的取用者程式碼。  
  
-   您可以使用隨附於 Visual c + + ITEST 公用程式。  
  
### <a name="to-use-the-itest-utility"></a>若要使用 ITEST 公用程式  
  
1.  開啟提供者的專案。  
  
2.  在**專案**功能表上，按一下 **設定**。  
  
3.  在**屬性頁**對話方塊中，按一下 [**偵錯**] 索引標籤。  
  
4.  在**偵錯工作階段的可執行檔**方塊中，選取 ITEST 應用程式。  
  
5.  設定中斷點、，然後如常進行偵錯。  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
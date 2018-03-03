---
title: "測試修改過的 ATL DHTML 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5ecb8526ec82e0f2d18c5306a94dd7f0160803b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="testing-the-modified-atl-dhtml-control"></a>測試修改過的 ATL DHTML 控制項
試試看您新的控制項，以查看它如何運作。  
  
#### <a name="to-build-and-test-the-modified-control"></a>若要建置並測試修改過的控制項  
  
1.  重建專案，並在測試容器中開啟它。 請參閱[使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如何存取測試容器的資訊。  
  
     調整大小以顯示所有您加入的按鈕控制項。  
  
2.  請檢查您所更改 HTML 插入兩個按鈕。 每個按鈕具有您在所識別的標籤[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md):**重新整理**和**HelloHTML**。  
  
3.  測試兩個新的按鈕，以查看其運作方式。  
  
 現在測試不屬於 UI 的方法。  
  
1.  反白顯示控制項，以便啟動框線。  
  
2.  在**控制項**功能表上，按一下 **叫用方法**。  
  
 標示為清單中的方法**方法名稱**容器可以呼叫的方法：`MethodInvoked`和`GoToURL`。 所有其他的方法是由 UI 控制。  
  
1.  選取方法來叫用，並按一下`Invoke`顯示方法的訊息方塊，或瀏覽至 www.microsoft.com。  
  
2.  在**叫用方法**對話方塊中，按一下 **關閉**。  
  
 若要深入了解各種項目和 ATL DHTML 控制項所組成的檔案，請參閱[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
## <a name="see-also"></a>請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)


---
title: "ATL DHTML 控制項的修改 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74ed32c0322d23cd3da1d439dcc8d8eadb246c13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="modifying-the-atl-dhtml-control"></a>修改 ATL DHTML 控制項
ATL 控制項精靈提供起始程式碼，並讓您可以建置並執行控制項，您可以看到專案檔中寫入方法的方式與 DHTML 方式呼叫控制項的 c + + 程式碼使用分派方法。 您可以新增任何分派方法的介面。 然後，您可以呼叫 HTML 資源中的方法。  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>若要修改 ATL DHTML 控制項  
  
1.  在 類別檢視中，展開控制項專案。  
  
     請注意，在"UI"結尾的介面的一種方法， `OnClick`。 結尾不是"I"的介面並沒有任何方法。  
  
2.  將方法呼叫`MethodInvoked`介面的結尾不是 「 UI。 」  
  
     這個方法會加入至控制項容器中用於容器互動，而不 DHTML 用於與控制項互動的介面的介面。 只有容器可以叫用這個方法。  
  
3.  在.cpp 檔案中尋找出附加虛設常式方法，並加入程式碼以顯示訊息方塊中，例如：  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  加入另一個方法呼叫`HelloHTML`，這次，將它加入至介面結束於 「 UI。 」 尋找附加虛設常式超出`HelloHTML`方法在.cpp 檔案，然後加入程式碼以顯示訊息方塊中，例如：  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  將第三個方法，加入`GoToURL`，結尾不是 「 UI。 」 介面 實作這個方法透過呼叫[IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx)、，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     您可以使用**IWebBrowser2**方法因為 ATL.h 檔案中為您提供該介面的指標。  
  
 接下來，修改 HTML 資源來叫用您所建立的方法。 您會加入三個按鈕叫用這些方法。  
  
#### <a name="to-modify-the-html-resource"></a>若要修改 HTML 資源  
  
1.  在 [方案總管] 中，按兩下要顯示的 HTML 資源的.htm 檔案。  
  
     檢查 HTML，特別是呼叫外部 Windows 分派方法。 HTML 呼叫專案的`OnClick`方法與參數表示控制項的主體 (`theBody`) 並指派色彩 (「`red`")。 方法呼叫之後的文字會出現在按鈕的標籤。  
  
2.  加入另一個`OnClick`方法，只會變更色彩。 例如:   
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     這個方法會建立標示的按鈕**重新整理**，使用者可以按一下以返回原始的白色背景的控制項。  
  
3.  將呼叫加入`HelloHTML`您所建立的方法。 例如:   
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     這個方法會建立標示的按鈕**HelloHTML**，使用者可以按一下以顯示`HelloHTML`訊息方塊。  
  
 您現在可以建置和[測試修改過的 DHTML 控制項](../atl/testing-the-modified-atl-dhtml-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)


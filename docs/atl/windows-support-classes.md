---
title: "Windows 支援類別 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b64654f0f483ec401b379ec4c512489ce8cac823
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="windows-support-classes"></a>Windows 支援類別
下列類別會提供適用於 windows 的支援：  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md)提供包裝函式**CreateWindow**和**CreateWindowEx**。  
  
-   [CWindow](../atl/reference/cwindow-class.md)包含用於管理視窗的方法。 `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基底類別。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md)實作新的視窗類別為基礎的視窗。 也可讓您以子類別化或超級類別視窗。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md)可實作對話方塊。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)可實作對話方塊 （強制或非強制回應） 裝載 ActiveX 控制項。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md)可實作對話方塊 （強制或非強制回應） 的基本功能。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md)操作裝載 ActiveX 控制項的視窗。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md)提供方法來管理裝載 ActiveX 控制項，而且具有支援裝載已授權的 ActiveX 控制項的視窗。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)實作包含在另一個物件內的視窗。  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的視窗類別資訊。  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md)支援動態鏈結的訊息對應。  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md)允許的物件來公開其訊息對應至其他物件。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md)提供簡單的方法，來標準化 ATL 視窗物件的特性。  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供預設值，如視窗樣式，以及用來建立視窗的延伸的樣式。 這些值會加入，使用邏輯 OR 運算子，以在視窗的建立期間所提供的值。  
  
## <a name="related-articles"></a>相關文章  
 [ATL 視窗類別](../atl/atl-window-classes.md)  
  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../atl/atl-class-overview.md)   
 [訊息對應巨集](../atl/reference/message-map-macros-atl.md)   
 [視窗類別巨集](../atl/reference/window-class-macros.md)


---
title: ATL 視窗類別簡介 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9b275831aee3ea96da1036019db07f9e2dfc93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356682"
---
# <a name="introduction-to-atl-window-classes"></a>ATL 視窗類別簡介
下列的 ATL 類別的實作和管理 windows 設計的：  
  
-   [CWindow](../atl/reference/cwindow-class.md)可讓您附加的視窗控制代碼`CWindow`物件。 然後呼叫`CWindow`管理視窗的方法。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md)可讓您實作新的視窗，並處理訊息的訊息對應。 您可以建立視窗為基礎的新 Windows 類別、 超級類別現有的類別或子類別現有的視窗。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md)可讓您實作獨佔或非強制回應對話方塊方塊和處理訊息與訊息對應。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)是預先建立的類別，另一個類別中實作包含其訊息對應的視窗。 使用`CContainedWindowT`可讓您集中管理某一個類別中的訊息處理。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)可讓您實作裝載 ActiveX 控制項對話方塊中 （強制或非強制回應）。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md)可讓您實作的基本功能的強制回應對話方塊。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md)可讓您實作裝載 ActiveX 控制項的視窗。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md)可讓您實作裝載授權的 ActiveX 控制項的視窗。  
  
 特定的視窗除了類別之外，ATL 提供許多設計是為了讓您更輕鬆 ATL 視窗物件的實作。 分別為：  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的視窗類別資訊。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md)和[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供標準化的特性，ATL 視窗物件的簡單方法。  
  
## <a name="see-also"></a>另請參閱  
 [視窗類別](../atl/atl-window-classes.md)


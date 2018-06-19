---
title: C + + 程式碼呼叫 DHTML |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9e369396c68a041dc5fe027802859c6071e50e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355457"
---
# <a name="calling-c-code-from-dhtml"></a>從 DHTML 呼叫 c + + 程式碼
DHTML 控制項可以裝載於容器，例如測試容器或 Internet Explorer。 請參閱[使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如何存取測試容器的資訊。  
  
 裝載控制項的容器會使用一般控制項介面的控制項與通訊。 DHTML 會使用分派介面結尾為"UI"，與您的 c + + 程式碼和 HTML 資源通訊。 在[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)，您將能練習將方法加入至被呼叫這些不同的介面。  
  
 若要查看的 DHTML，從呼叫 c + + 程式碼範例[建立 DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)使用 ATL 控制項精靈，並檢查 HTML 檔和標頭檔中的程式碼。  
  
## <a name="declaring-webbrowser-methods-in-the-header-file"></a>宣告的標頭檔中的 WebBrowser 方法  
 要叫用 c + + 方法，從 DHTML UI，您必須將方法加入至控制項的 UI 介面。 例如，ATL 控制項精靈所建立的標頭檔包含 c + + 方法`OnClick`，即 UI 控制項介面的精靈產生的成員。  
  
 檢查`OnClick`控制的.h 檔案中：  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]  
  
 第一個參數， `pdispBody`，主體物件的分派介面的指標。 第二個參數， `varColor`，識別要套用至控制項的色彩。  
  
## <a name="calling-c-code-in-the-html-file"></a>HTML 檔案中呼叫 c + + 程式碼  
 一旦您已經宣告的標頭檔中的 WebBrowser 方法，您可以叫用的方法，從 HTML 檔案。 請注意，在 HTML 檔案 ATL 控制項精靈插入三個 Windows 分派方法： 三個`OnClick`訊息分派至變更控制項的背景色彩的方法。  
  
 請檢查 HTML 檔案中的方法：  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 上方視窗外部方法的 HTML 程式碼`OnClick`，稱為按鈕標籤的一部分。 方法有兩個參數： `theBody`，會參考的 HTML 文件主體和`"red"`，表示該控制項的背景色彩時就會變更為紅色按鈕。 `Red`下列標記是按鈕的標籤。  
  
 請參閱[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)如需有關提供您自己的方法。 請參閱[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)如需有關 HTML 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)


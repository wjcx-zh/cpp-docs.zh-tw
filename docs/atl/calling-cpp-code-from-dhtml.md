---
title: 從 DHTML 呼叫 c + + 程式碼
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: 0fa4f51f4488be61edb0f01d9fddc956cd7a45b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555190"
---
# <a name="calling-c-code-from-dhtml"></a>從 DHTML 呼叫 c + + 程式碼

DHTML 控制項可以裝載在容器中，例如測試容器或 Internet Explorer。 請參閱[以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如需有關如何測試容器存取資訊。

裝載控制項的容器會使用一般控制項介面的控制項與通訊。 DHTML 使用分派介面的結尾是"UI"，與您的 c + + 程式碼和 HTML 資源進行通訊。 在 [修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)，您將能練習加入由這些不同的介面呼叫方法。

從 DHTML 呼叫 c + + 程式碼的範例，請參閱[建立 DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)使用 ATL 控制項精靈，並檢查標頭檔，並在 HTML 檔案中的程式碼。

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>宣告的標頭檔中的 WebBrowser 方法

要叫用 c + + 方法，從 DHTML UI，您必須將方法加入至控制項的 UI 介面。 例如，ATL 控制項精靈所建立的標頭檔包含 c + + 方法`OnClick`，這是 UI 控制項的介面精靈產生的成員。

檢查`OnClick`控制的.h 檔案中：

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

第一個參數， *pdispBody*，是主體物件的分派介面的指標。 第二個參數， *varColor*，識別要套用至控制項的色彩。

## <a name="calling-c-code-in-the-html-file"></a>HTML 檔案中呼叫 c + + 程式碼

一旦您宣告的標頭檔中的 WebBrowser 方法時，您可以叫用的方法，從 HTML 檔案。 請注意，在 HTML 檔案，ATL 控制項精靈就會插入三個 Windows 分派方法： 三個`OnClick`，分派訊息以變更控制項的背景色彩的方法。

請檢查其中一個 HTML 檔中的方法：

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

在視窗外部方法中，上述的 HTML 程式碼`OnClick`，稱為按鈕標記的一部分。 方法有兩個參數： `theBody`，會參考的 HTML 文件中，主體和`"red"`，這表示，控制項的背景色彩會變更為紅色按一下按鈕時。 `Red`下列標記是按鈕的標籤。

請參閱[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)如需有關提供您自己的方法。 請參閱[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)的 HTML 檔案的詳細資訊。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)


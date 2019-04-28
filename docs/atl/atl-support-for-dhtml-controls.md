---
title: DHTML 控制項的 ATL 支援
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223286"
---
# <a name="atl-support-for-dhtml-controls"></a>DHTML 控制項的 ATL 支援

使用 ATL，您可以透過動態 HTML (DHTML) 功能建立控制項。 ATL DHTML 控制項：

- 裝載 WebBrowser 控制項。

- 指定使用 HTML，DHTML 控制項的使用者介面 (UI)。

- 透過其介面中，存取 WebBrowser 物件和其方法[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))。

- 管理之間的通訊C++程式碼和 HTML。

DHTML 控制項是類似於其他 ATL 控制項，除了 DHTML 控制項包含額外的分派介面。 請參閱中的圖表[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)如需預設 DHTML 專案中所提供的介面。

您可以檢視 ATL DHTML 控制項在網頁瀏覽器或其他容器，例如 ActiveX 控制項測試容器中。

## <a name="in-this-section"></a>本節內容

[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
描述 DHTML 控制項專案的項目。

[從 DHTML 呼叫 C++ 程式碼](../atl/calling-cpp-code-from-dhtml.md)<br/>
提供呼叫的範例C++從 DHTML 控制項的程式碼。

[建立 ATL DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)<br/>
列出用來建立 DHTML 控制項的步驟。

[測試 ATL DHTML 控制項](../atl/testing-the-atl-dhtml-control.md)<br/>
示範如何建置和測試初始的 DHTML 控制項專案。

[修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)<br/>
示範如何加入控制項新功能。

[測試已改變的 ATL DHTML 控制項](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
示範如何建置和測試控制項的新增的功能。

## <a name="related-sections"></a>相關章節

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

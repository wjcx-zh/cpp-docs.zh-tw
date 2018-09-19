---
title: DHTML 控制項的 ATL 支援 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 281b767151726f695e23c4cf2b2df26f8690c5c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063992"
---
# <a name="atl-support-for-dhtml-controls"></a>DHTML 控制項的 ATL 支援

使用 ATL，您可以透過動態 HTML (DHTML) 功能建立控制項。 ATL DHTML 控制項：

- 裝載 WebBrowser 控制項。

- 指定使用 HTML，DHTML 控制項的使用者介面 (UI)。

- 透過其介面中，存取 WebBrowser 物件和其方法[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。

- 管理 c + + 程式碼與 HTML 之間的通訊。

DHTML 控制項是類似於其他 ATL 控制項，除了 DHTML 控制項包含額外的分派介面。 請參閱中的圖表[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)如需預設 DHTML 專案中所提供的介面。

您可以檢視 ATL DHTML 控制項在網頁瀏覽器或其他容器，例如 ActiveX 控制項測試容器中。

## <a name="in-this-section"></a>本節內容

[識別 DHTML 控制項專案的項目](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
描述 DHTML 控制項專案的項目。

[從 DHTML 呼叫 C++ 程式碼](../atl/calling-cpp-code-from-dhtml.md)<br/>
提供呼叫 DHTML 控制項的 c + + 程式碼範例。

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


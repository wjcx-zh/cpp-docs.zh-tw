---
title: HOW TO：建置免註冊 COM 元件
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 503c3e4399359d793ce660f36844d2edc6602146
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416765"
---
# <a name="how-to-build-registration-free-com-components"></a>HOW TO：建置免註冊 COM 元件

免註冊 COM 元件是內建於 Dll 的資訊清單的 COM 元件。

### <a name="to-build-manifests-into-com-components"></a>建置 COM 元件的資訊清單

1. 開啟專案屬性頁之 COM 元件。

1. 依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。

1. 選取 **輸入和輸出**屬性頁面中，然後再把**內嵌資訊清單**屬性等於**是**。

1. 按一下 [確定] 。

1. 建置方案。

## <a name="see-also"></a>另請參閱

[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)<br/>
[關於並排顯示的組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[如何：建置隔離的應用程式以取用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)

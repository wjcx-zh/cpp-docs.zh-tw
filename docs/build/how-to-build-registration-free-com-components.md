---
title: 如何： 建置免註冊 COM 元件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a9e1769ff0ba9a0589f9d59c3d1f1ed2fc5bcb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699851"
---
# <a name="how-to-build-registration-free-com-components"></a>如何：建置免註冊的 COM 元件

免註冊 COM 元件是內建於 Dll 的資訊清單的 COM 元件。

### <a name="to-build-manifests-into-com-components"></a>建置 COM 元件的資訊清單

1. 開啟專案屬性頁之 COM 元件。

1. 依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。

1. 選取 **輸入和輸出**屬性頁面中，然後再把**內嵌資訊清單**屬性等於**是**。

1. 按一下 [確定 **Deploying Office Solutions**]。

1. 建置方案。

## <a name="see-also"></a>另請參閱

[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)<br/>
[關於並排顯示的組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[如何：建置隔離的應用程式以使用 COM 元件](../build/how-to-build-isolated-applications-to-consume-com-components.md)
---
title: HOW TO：建置隔離的應用程式以使用 COM 元件
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 01b5c7056bd10a7c1f88df74b5c6b4aa78ff3fde
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273556"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>HOW TO：建置隔離的應用程式以使用 COM 元件

隔離的應用程式是內建於程式資訊清單的應用程式。 您可以建立隔離的應用程式以使用 COM 元件。

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>加入 COM 參考，以隔離的應用程式資訊清單

1. 開啟隔離的應用程式的專案屬性頁。

1. 依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。

1. 選取 **隔離的 COM**屬性頁面中，然後再把**元件的檔案名稱**屬性設為您想要隔離的應用程式使用之 COM 元件的名稱。

1. 按一下 [確定] 。

### <a name="to-build-manifests-into-isolated-applications"></a>若要在隔離的應用程式中建置資訊清單

1. 開啟隔離的應用程式的專案屬性頁。

1. 依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。

1. 選取 **輸入和輸出**屬性頁面中，然後再把**內嵌資訊清單**屬性等於**是**。

1. 按一下 [確定] 。

1. 建置方案。

## <a name="see-also"></a>另請參閱

[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)<br/>
[關於並排顯示的組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)

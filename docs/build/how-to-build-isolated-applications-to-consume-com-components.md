---
title: 如何：建置隔離的應用程式以使用 COM 元件
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 8ae3c51502267f202cbb85ea7be2a81dc3310410
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493240"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：建置隔離的應用程式以使用 COM 元件

隔離的應用程式是在程式中內建資訊清單的應用程式。 您可以建立隔離的應用程式以使用 COM 元件。

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>將 COM 參考新增至隔離應用程式的資訊清單

1. 開啟隔離應用程式的專案屬性頁。

1. 展開 [設定**屬性**] 節點，然後展開 [**資訊清單工具**] 節點。

1. 選取 [**隔離的 COM** ] 屬性頁，然後將 [**元件檔名稱**] 屬性設定為您要隔離應用程式使用的 COM 元件名稱。

1. 按一下 [確定]  。

### <a name="to-build-manifests-into-isolated-applications"></a>將資訊清單組建到隔離的應用程式

1. 開啟隔離應用程式的專案屬性頁。

1. 展開 [設定**屬性**] 節點，然後展開 [**資訊清單工具**] 節點。

1. 選取 [**輸入和輸出**] 屬性頁，然後將 [**內嵌資訊清單**] 屬性設為等於 **[是]**。

1. 按一下 [確定]  。

1. 建置方案。

## <a name="see-also"></a>請參閱

[隔離的應用程式](/windows/win32/SbsCs/isolated-applications)<br/>
[關於並存元件](/windows/win32/SbsCs/about-side-by-side-assemblies-)

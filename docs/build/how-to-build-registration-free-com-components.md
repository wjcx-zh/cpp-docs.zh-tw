---
title: 如何：建置免註冊的 COM 元件
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188934"
---
# <a name="how-to-build-registration-free-com-components"></a>如何：建置免註冊的 COM 元件

免註冊的 COM 元件是 COM 元件，其中包含內建在 Dll 中的資訊清單。

### <a name="to-build-manifests-into-com-components"></a>將資訊清單建立為 COM 元件

1. 開啟 COM 元件的專案屬性頁。

1. 展開 [設定**屬性**] 節點，然後展開 [**資訊清單工具**] 節點。

1. 選取 [**輸入和輸出**] 屬性頁，然後將 [**內嵌資訊清單**] 屬性設為等於 **[是]**。

1. 按一下 [確定]  。

1. 建置方案。

## <a name="see-also"></a>請參閱

[如何：建置隔離的應用程式以使用 COM 元件](how-to-build-isolated-applications-to-consume-com-components.md)

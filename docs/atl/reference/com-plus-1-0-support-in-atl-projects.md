---
title: COM + 1.0 支援 ATL 專案中
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 4bc7683d6121dec748e30c1ea717042b9cf1ecbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562457"
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支援 ATL 專案中

您可以使用[ATL 專案精靈](../../atl/reference/creating-an-atl-project.md)來建立專案的 COM + 1.0 元件的基本支援。

COM + 1.0 被設計來開發元件為基礎的分散式應用程式。 它也會提供部署和管理這些應用程式的執行階段基礎結構。

如果您選取**支援 COM + 1.0**核取方塊，精靈會修改建置指令碼在連結步驟。 具體來說，COM + 1.0 專案會連結至下列的程式庫：

- comsvcs.lib

- Mtxguid.lib

如果您選取**支援 COM + 1.0**核取方塊，您也可以選取**支援元件登錄器**。 支援元件登錄器可讓您的 COM + 1.0 物件，以取得一份元件、 註冊元件，或取消登錄元件 （個別或全部一次）。

## <a name="see-also"></a>另請參閱

[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)


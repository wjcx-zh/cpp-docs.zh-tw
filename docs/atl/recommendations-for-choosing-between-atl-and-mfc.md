---
title: ATL 和 MFC 之間選擇的建議
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: b3c01a54c1250ae97d5377cb0b1ff49a17c3f7c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468246"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>ATL 和 MFC 之間選擇的建議

當開發元件和應用程式時，您可以選擇兩種方法 — ATL 和 MFC （Microsoft Foundation 類別程式庫）。

## <a name="using-atl"></a>使用 ATL

ATL 是迅速、 輕鬆的方式，來建立 c + + 中的 COM 元件和維護較小的使用量。 若要建立的控制項，如果您不需要的所有內建功能，MFC 會自動提供使用 ATL。

## <a name="using-mfc"></a>使用 MFC

MFC 可讓您建立完整的應用程式、 ActiveX 控制項和主動式文件。 如果您已經使用 MFC 建立控制項，您可能想要在 MFC 中繼續開發。 當建立新的控制項，請考慮使用 ATL，如果您不需要的所有 MFC 的內建功能。

## <a name="using-atl-in-an-mfc-project"></a>MFC 專案中使用 ATL

您可以新增支援在現有的 MFC 專案中使用 ATL，透過執行精靈。 如需詳細資訊，請參閱 <<c0> [ 將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

## <a name="see-also"></a>另請參閱

[ATL 簡介](../atl/introduction-to-atl.md)


---
title: 從 CObject 衍生類別的成本多高？
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 8f83bf9ee522487761aaa865a8315a174a47302d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446050"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>從 CObject 衍生類別的成本多高？

衍生自[CObject](../mfc/reference/cobject-class.md)類別的額外負荷很小。 您的衍生類別只會繼承四個虛擬函數和一個[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件。

## <a name="see-also"></a>另請參閱

[CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

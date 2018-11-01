---
title: 從 CObject 衍生類別的成本多高？
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 521b6a32e3e5b34b4da9dab3117d55a728bd8e88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500443"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>從 CObject 衍生類別的成本多高？

衍生自類別的額外負荷[CObject](../mfc/reference/cobject-class.md)非常少。 您的衍生的類別繼承只有四個虛擬函式和一個[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件。

## <a name="see-also"></a>另請參閱

[CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

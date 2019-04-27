---
title: 從 CObject 衍生類別的成本多高？
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: de760a2fd2908595314dc09cf5a317da3581e3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186045"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>從 CObject 衍生類別的成本多高？

衍生自類別的額外負荷[CObject](../mfc/reference/cobject-class.md)非常少。 您的衍生的類別繼承只有四個虛擬函式和一個[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件。

## <a name="see-also"></a>另請參閱

[CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

---
title: 從 CObject 衍生類別的成本多高？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffff35cdef6cf2f730687334bbb56bc078371a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381673"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>從 CObject 衍生類別的成本多高？
衍生自類別的額外負荷[CObject](../mfc/reference/cobject-class.md)降至最低。 您的衍生的類別會繼承，只能有四個虛擬函式和單一[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)物件。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

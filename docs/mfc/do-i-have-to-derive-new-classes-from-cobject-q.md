---
title: 我必須從 CObject 衍生新類別嗎？
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446933"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我必須從 CObject 衍生新類別嗎？

不，不用。

當您需要它所提供的功能（例如序列化或動態建立）時，從[CObject](../mfc/reference/cobject-class.md)衍生類別。 許多資料類別需要序列化至檔案，因此從 `CObject` 衍生通常是不錯的作法。 如需衍生自 `CObject`之類別的範例，請參閱「[自由曲線」範例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

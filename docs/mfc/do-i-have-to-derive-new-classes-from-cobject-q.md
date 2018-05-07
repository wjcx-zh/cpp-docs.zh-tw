---
title: 我必須從 CObject 衍生新類別嗎？ | Microsoft Docs
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
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51904ac06ae6c2db5586f8dc405f85145c5b1f30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我必須從 CObject 衍生新類別嗎？
不，不用。  
  
 自[CObject](../mfc/reference/cobject-class.md)當您需要其提供例如序列化或動態時的功能。 許多資料類別需要序列化至檔案，因此從 `CObject` 衍生通常是不錯的作法。 類別的範例衍生自`CObject`，請參閱[Scribble 範例](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)

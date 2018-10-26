---
title: 建立堆疊和佇列集合 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96bcaf768ece46c22422fb3d98b85def7c57ed6b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056590"
---
# <a name="creating-stack-and-queue-collections"></a>建立堆疊和佇列集合

這篇文章說明如何建立其他資料結構，例如[堆疊](#_core_stacks)並[佇列](#_core_queues)，從 MFC 清單類別。 這些範例會使用衍生自 `CList` 的類別，不過除非您需要新增其他功能，否則您可以直接使用 `CList`。

##  <a name="_core_stacks"></a> 堆疊

因為標準的清單集合具有一個頭部和尾部，建立模擬後進先出的堆疊行為之衍生清單集合是很容易的。 堆疊就像自助餐廳的一疊盤子。 當餐盤加入堆疊時，它們會位於堆疊的上方。 最後加入的盤子是第一個被移除的盤子。 清單集合成員函式 `AddHead` 和 `RemoveHead` 可用來從清單的開頭明確地加入和移除項目；因此，最新加入的項目會最先被移除。

#### <a name="to-create-a-stack-collection"></a>建立堆疊集合

1. 從其中一個現有的 MFC 清單類別衍生新的清單類別，並加入多個成員函式支援堆疊作業的功能。

   下列範例顯示如何加入成員函式，以推入項目至堆疊、檢視堆疊的最上層項目，並從堆疊最上方彈出項目：

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

請注意，這種方法會公開基礎 `CObList` 類別。 使用者可以呼叫任何 `CObList` 成員函式，無論它是否對堆疊具有意義。

##  <a name="_core_queues"></a> 佇列

因為標準清單集合具有一個頭部和尾部，建立模擬先進先出的佇列行為之衍生清單集合也是很容易的。 佇列就像是在自助餐廳排隊的人。 隊伍中的第一個人會是第一個被服務的人。 當更多人來的時候，他們會走到隊伍的尾端等待。 清單集合成員函式 `AddTail` 和 `RemoveHead` 可用來從清單的開頭或尾端明確地加入和移除項目；因此，最新加入的項目會最後被移除。

#### <a name="to-create-a-queue-collection"></a>建立佇列集合

1. 從其中一個預先定義的清單類別衍生隨附 MFC 程式庫之新的清單類別，並加入多個成員函式支援佇列作業。

   下列範例顯示如何附加成員函式，將項目加入至佇列的末端，並從佇列的前端取得項目。

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>另請參閱

[集合](../mfc/collections.md)


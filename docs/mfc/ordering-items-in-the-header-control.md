---
title: 排序標題控制項中的項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60139821c1b15673fac0fb8f9ec3925cbfa6dc31
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052093"
---
# <a name="ordering-items-in-the-header-control"></a>排序標題控制項中的項目

之後，您就[項目新增至標題控制項](../mfc/adding-items-to-the-header-control.md)，您可以操作或取得它們的順序，使用下列函式的相關資訊：

- [Cheaderctrl:: Getorderarray](../mfc/reference/cheaderctrl-class.md#getorderarray)和[cheaderctrl:: Setorderarray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   以由左至右的順序擷取和設定標題項目。

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex)。

   擷取特定標頭項目的索引值。

除了先前的成員函式，HDS_DRAGDROP 樣式可讓使用者拖放標題控制項內的標頭項目。 如需詳細資訊，請參閱 <<c0> [ 提供的標頭項目拖放支援](../mfc/providing-drag-and-drop-support-for-header-items.md)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)


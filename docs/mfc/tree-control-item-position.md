---
title: 樹狀目錄控制項目位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e24c21a8a44f09e9141b1763646d1a887bda158
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412089"
---
# <a name="tree-control-item-position"></a>樹狀目錄控制項目位置

項目的初始位置設定的項目會新增至樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 使用`InsertItem`成員函式。 成員函式呼叫指定的父項目的控制代碼和要插入新項目之後的項目控點。 第二個控制代碼必須找出指定的父代的其中一個子項目，或其中一個值： `TVI_FIRST`， `TVI_LAST`，或`TVI_SORT`。

當`TVI_FIRST`或`TVI_LAST`指定時，樹狀結構控制項中將新的項目放置在開頭或結尾指定的父項目的子項目清單。 當`TVI_SORT`指定時，樹狀結構控制項中的項目標籤的文字為基礎的字母順序中的子項目清單中插入新項目。

您可以藉由呼叫父項目的子項目清單將放入依字母順序排列的順序[SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren)成員函式。 此函式包含參數，指定所有層級的子項目遞減從指定的父項目也會依字母順序排序。

[SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb)成員函式可讓您根據您定義的準則的子系項目排序。 當您呼叫此函式時，您會指定兩個子項目的相對順序必須決定時，可以呼叫樹狀結構控制項中的應用程式定義的回呼函式。 回呼函式會接收兩個 32 位元應用程式定義值進行比較的項目和第三個 32 位元值，這個值呼叫時，您會指定`SortChildrenCB`。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


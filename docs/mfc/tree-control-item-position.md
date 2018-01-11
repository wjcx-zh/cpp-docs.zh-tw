---
title: "樹狀目錄控制項目位置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db47e27ad0b556e08f51685bf84b6bd998722239
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-position"></a>樹狀目錄控制項目位置
當項目加入樹狀結構控制項中設定項目的初始位置 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 使用`InsertItem`成員函式。 成員函式呼叫指定的父項目控點，而且要插入新項目之後的項目控制代碼。 第二個控制代碼必須找出給定的父代的其中一個子項目，或其中一個值： `TVI_FIRST`， `TVI_LAST`，或`TVI_SORT`。  
  
 當`TVI_FIRST`或`TVI_LAST`指定時，樹狀目錄控制項的開頭或結尾指定的父項目的子項目清單會將新的項目。 當`TVI_SORT`指定時，樹狀結構控制項中的項目標籤的文字為基礎的字母順序中的子項目清單中插入新項目。  
  
 您可以藉由呼叫子項目的父項目清單將放入字母順序[SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren)成員函式。 此函式包含參數，指定所有層級的子項目遞減從指定的父項目也會依字母順序排序。  
  
 [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb)成員函式可讓您根據您定義的準則的子系項目排序。 當您呼叫此函式時，您可以指定每當必須決定兩個子項目的相對順序，可以呼叫樹狀結構控制項中的應用程式定義的回呼函式。 回呼函式會接收兩個 32 位元應用程式定義值進行比較的項目和第三個 32 位元值，呼叫時，您指定`SortChildrenCB`。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)


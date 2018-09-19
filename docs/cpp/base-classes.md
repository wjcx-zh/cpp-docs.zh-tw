---
title: 基底類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6d6494cc1ef371cfeb51647bc310a74ac68bfb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059194"
---
# <a name="base-classes"></a>基底類別

繼承的程序會建立新的衍生類別，該類別是由基底類別的成員再加上由衍生類別加入的任何新成員所組成。 在多重繼承中可以建構繼承圖形，其中相同的基底類別是屬於多個衍生類別的一部分。 下圖顯示這類圖形。

![基底類別的多個執行個體](../cpp/media/vc38xn1.gif "vc38XN1")單一基底類別的多個執行個體

圖中以圖示表示 `CollectibleString` 和 `CollectibleSortable` 的各個元件。 不過，位於 `Collectible` 中的基底類別 `CollectibleSortableString` 是透過 `CollectibleString` 路徑和 `CollectibleSortable` 路徑存取。 若要消除這種冗餘狀況，可以在繼承時將這些類別宣告為虛擬基底類別。
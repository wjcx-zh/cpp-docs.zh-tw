---
title: 基底類別
ms.date: 11/19/2018
helpviewer_keywords:
- inheritance, multiple
- base classes [C++], virtual
- derived classes [C++], multiple bases
- multiple inheritance, base classes
- virtual base classes [C++]
- base classes [C++]
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
ms.openlocfilehash: 50bddef3ea1ee1462d8cf115c0980270c8deab25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181469"
---
# <a name="base-classes"></a>基底類別

繼承的程序會建立新的衍生類別，該類別是由基底類別的成員再加上由衍生類別加入的任何新成員所組成。 在多重繼承中可以建構繼承圖形，其中相同的基底類別是屬於多個衍生類別的一部分。 下圖顯示這類圖形。

![基類的多個實例](../cpp/media/vc38xn1.gif "單一基底類別的多個執行個體") <br/>
單一基類的多個實例

圖中以圖示表示 `CollectibleString` 和 `CollectibleSortable` 的各個元件。 不過，位於 `Collectible` 中的基底類別 `CollectibleSortableString` 是透過 `CollectibleString` 路徑和 `CollectibleSortable` 路徑存取。 若要消除這種冗餘狀況，可以在繼承時將這些類別宣告為虛擬基底類別。

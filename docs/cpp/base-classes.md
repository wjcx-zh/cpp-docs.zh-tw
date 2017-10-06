---
title: "基底類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6b08321ffb027901683a4f85960579625ce98cc2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="base-classes"></a>基底類別
繼承的程序會建立新的衍生類別，該類別是由基底類別的成員再加上由衍生類別加入的任何新成員所組成。 在多重繼承中可以建構繼承圖形，其中相同的基底類別是屬於多個衍生類別的一部分。 下圖顯示這類圖形。  
  
 ![基底類別的多個執行個體](../cpp/media/vc38xn1.gif "vc38XN1")  
單一基底類別的多個執行個體  
  
 圖中以圖示表示 `CollectibleString` 和 `CollectibleSortable` 的各個元件。 不過，位於 `Collectible` 中的基底類別 `CollectibleSortableString` 是透過 `CollectibleString` 路徑和 `CollectibleSortable` 路徑存取。 若要消除這種冗餘狀況，可以在繼承時將這些類別宣告為虛擬基底類別。  
  


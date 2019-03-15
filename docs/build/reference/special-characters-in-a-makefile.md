---
title: Makefile 中的特殊字元
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: d915b182d72b4251f416433642cd8b1832b80e08
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824714"
---
# <a name="special-characters-in-a-makefile"></a>Makefile 中的特殊字元

若要使用 NMAKE 特殊字元常值字元，請在其前面放置插入號 (^)。 NMAKE 會忽略在其他字元前面的插入號。 特殊字元如下：

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

加上引號的字串中的插入號 (^) 會被視為常值的插入號字元。 行結尾處的插入號會插入常值的新行字元字串或巨集。

在巨集中，反斜線 (\\) 接著新行字元取代空格。

在命令中，百分比符號 （%）為檔案指定名稱。 若要表示 %命令解譯為常值中的，指定雙百分比符號 （%）取代一個。 在其他情況下，NMAKE 解譯單一 %解譯為常值，但一律會解譯雙精度浮點數 %%做為單一 %。 因此，來代表常值 %%，指定任一個的三個百分比符號，%%%，或四個百分比符號 %%%。

若要使用貨幣符號 （$），在命令中的常值字元，指定兩個貨幣符號 （$$）。 這個方法也可用在其他情況下，^ $ 運作。

## <a name="see-also"></a>另請參閱

[Makefile 內容](contents-of-a-makefile.md)

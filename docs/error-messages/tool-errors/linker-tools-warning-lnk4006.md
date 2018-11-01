---
title: 連結器工具警告 LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: c81c93a6df8c7eef809f243e3dc56164ea548371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472224"
---
# <a name="linker-tools-warning-lnk4006"></a>連結器工具警告 LNK4006

符號已定義於物件;忽略的第二個定義

以其裝飾形式顯示的 `symbol` 已定義多次。 發生這個警告時，`symbol`兩次，將會加入，但是只有其第一個表單將會使用。

如果您嘗試合併成一個的兩個匯入程式庫，您可以取得這項警告。

如果您重建 C 執行階段程式庫，您可以忽略此訊息。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 給定`symbol`可能是封裝函式，建立與編譯[/Gy](../../build/reference/gy-enable-function-level-linking.md)。 此符號會包含一個以上的檔案中，但編譯之間不同。 重新編譯包含的所有檔案`symbol`。

1. 指定`symbol`可能已經定義以不同的方式在不同的程式庫中的兩個成員物件中。

1. 絕對可能已經定義兩次，以在每個定義不同的值。

1. 如果合併程式庫時，會收到錯誤訊息`symbol`已經存在於要新增至程式庫。
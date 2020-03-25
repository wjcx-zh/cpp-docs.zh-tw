---
title: 連結器工具警告 LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194313"
---
# <a name="linker-tools-warning-lnk4006"></a>連結器工具警告 LNK4006

符號已定義于物件中;已忽略第二個定義

以其裝飾形式顯示的 `symbol` 已定義多次。 當遇到此警告時，`symbol` 將會新增兩次，但只會使用其第一個表單。

如果您嘗試將兩個「匯入」程式庫合併成一個，就會收到這個警告。

如果您要重建 C 執行時間程式庫，可以忽略此訊息。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 給定的 `symbol` 可能是使用[/gy](../../build/reference/gy-enable-function-level-linking.md)編譯所建立的封裝函式。 這個符號已包含在一個以上的檔案中，但在編譯之間已變更。 重新編譯包含 `symbol`的所有檔案。

1. 給定的 `symbol` 可能已在不同程式庫中的兩個成員物件中以不同方式定義。

1. 絕對可能定義了兩次，每個定義中的值都不同。

1. 如果合併程式庫時收到錯誤訊息，`symbol` 已經存在於要加入的程式庫中。

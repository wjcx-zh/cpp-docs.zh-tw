---
title: 連結器工具警告 LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194183"
---
# <a name="linker-tools-warning-lnk4022"></a>連結器工具警告 LNK4022

找不到符號 ' symbol ' 的唯一相符項

連結或 LIB 找到指定之未修飾符號的多個相符專案，而且無法解決不明確的問題。 不會產生任何輸出檔（.exe、.dll、exp 或 .lib）。 這個警告後面會加上每個重複符號的一個警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) ，最後再接著嚴重的錯誤[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。

若要避免這個警告，請以其裝飾形式指定符號。 在物件上執行[DUMPBIN](../../build/reference/dumpbin-options.md) ，以查看裝飾名稱。

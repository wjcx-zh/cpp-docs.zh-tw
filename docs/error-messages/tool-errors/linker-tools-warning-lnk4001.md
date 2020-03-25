---
title: 連結器工具警告 LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194404"
---
# <a name="linker-tools-warning-lnk4001"></a>連結器工具警告 LNK4001

未指定任何物件檔案;使用的程式庫

連結器已傳遞一或多個 .lib 檔案，但沒有 .obj 檔案。

因為連結器無法存取 .lib 檔案中能夠存取 .obj 檔案中的資訊，所以這個警告表示您必須明確指定其他連結器選項。 例如，您可能必須指定[/MACHINE](../../build/reference/machine-specify-target-platform.md)、 [/out](../../build/reference/out-output-file-name.md)或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)選項。

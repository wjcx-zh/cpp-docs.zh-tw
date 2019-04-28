---
title: 連結器工具警告 LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298785"
---
# <a name="linker-tools-warning-lnk4001"></a>連結器工具警告 LNK4001

未指定; 的物件檔案使用程式庫

連結器傳遞了一個或多個的.lib 檔案，但沒有.obj 檔案。

連結器不能存取資訊的.lib 檔案中，它就能夠將.obj 檔案中存取，因為這則警告指出您必須明確指定 其他連結器選項。 例如，您可能需要指定[/機器](../../build/reference/machine-specify-target-platform.md)， [/out](../../build/reference/out-output-file-name.md)，或[/ENTRY](../../build/reference/entry-entry-point-symbol.md)選項。
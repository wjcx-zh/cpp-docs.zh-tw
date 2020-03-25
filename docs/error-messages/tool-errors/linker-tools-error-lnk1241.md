---
title: 連結器工具錯誤 LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183809"
---
# <a name="linker-tools-error-lnk1241"></a>連結器工具錯誤 LNK1241

已指定資源檔 ' resource file '

如果您從命令列手動執行**cvtres** ，然後將產生的 .obj 檔案傳遞至連結器，以及其他 .res 檔案，就會產生此錯誤。

若要指定多個 .res 檔案，請將它們全部傳遞至連結器作為 .res 檔案，而不是從**cvtres**所建立的 .obj 檔案中。

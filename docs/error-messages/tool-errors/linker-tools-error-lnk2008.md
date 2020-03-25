---
title: 連結器工具錯誤 LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194820"
---
# <a name="linker-tools-error-lnk2008"></a>連結器工具錯誤 LNK2008

修復目標未對齊 ' symbol_name '

連結在您的物件檔案中找到的修復目標未正確對齊。

此錯誤可能是因為自訂 secton 對齊（例如 #pragma [pack](../../preprocessor/pack.md)）、 [align](../../cpp/align-cpp.md)修飾詞，或使用修改 secton 對齊的元件語言程式碼所造成。

如果您的程式碼未使用上述任何一項，則這可能是由編譯器所造成。

---
title: 連結器工具錯誤 LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: fad8960424cd73240d547ef894b2ae5cdf358601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498266"
---
# <a name="linker-tools-error-lnk2039"></a>連結器工具錯誤 LNK2039

匯入的 ref 類別\<類型 >' 中所定義的.obj; 它應該是匯入或定義，而非兩者皆是

Ref 類別 ' <`type`>' 匯入指定的.obj 檔案中，但也會定義在另一個.obj 檔案中。 這種情況可能會造成執行階段錯誤或其他未預期的行為。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 檢查 '`type`' 是否必須定義於另一個 .obj 檔案，並檢查是否必須從 .winmd 檔案匯入它。

1. 移除定義或匯入。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[連結器工具錯誤 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
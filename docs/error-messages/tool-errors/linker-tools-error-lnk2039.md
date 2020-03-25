---
title: 連結器工具錯誤 LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194495"
---
# <a name="linker-tools-error-lnk2039"></a>連結器工具錯誤 LNK2039

匯入 ref 類別 '\<類型 > '，其定義于另一個 .obj;它應該是匯入或定義的，但不能同時是兩者

Ref 類別 ' <`type`> ' 已匯入指定的 .obj 檔案中，但也定義于另一個 .obj 檔案中。 這種情況可能會造成執行階段錯誤或其他未預期的行為。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 檢查 '`type`' 是否必須定義於另一個 .obj 檔案，並檢查是否必須從 .winmd 檔案匯入它。

1. 移除定義或匯入。

## <a name="see-also"></a>另請參閱

[連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[連結器工具錯誤 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)

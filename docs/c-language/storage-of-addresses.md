---
title: 位址的儲存
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148734"
---
# <a name="storage-of-addresses"></a>位址的儲存

位址所需的儲存數量和位址的意義取決於編譯器的實作。 不同類型的指標不一定會具有相同長度。 因此，**sizeof(char \*)** 不一定等於 **sizeof(int \*)**。

**Microsoft 專屬**

對於 Microsoft C 編譯器，**sizeof(char \*)** 等於 **sizeof(int \*)**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[指標宣告](../c-language/pointer-declarations.md)

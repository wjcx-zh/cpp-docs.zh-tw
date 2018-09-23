---
title: 位址的儲存 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe77d3775c489399bb8b9032e645eee17d70b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076589"
---
# <a name="storage-of-addresses"></a>位址的儲存

位址所需的儲存數量和位址的意義取決於編譯器的實作。 不同類型的指標不一定會具有相同長度。 因此，**sizeof(char \*)** 不一定等於 **sizeof(int \*)**。

**Microsoft 專屬**

對於 Microsoft C 編譯器，**sizeof(char \*)** 等於 **sizeof(int \*)**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[指標宣告](../c-language/pointer-declarations.md)
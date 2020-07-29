---
title: 類型 char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: 5b60af4becb3fa496a0b54c3702eac247bd75d5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231438"
---
# <a name="type-char"></a>類型 char

**`char`** 類型是用來儲存可表示字元集之成員的整數值。 該整數值是對應所指定字元的 ASCII 碼。

**Microsoft 特定的**

類型的字元值的 **`unsigned char`** 範圍是從0到0xff 的十六進位。 的 **`signed char`** 範圍是0x80 到0x7f。 這些範圍會分別轉譯為十進位的 0 到 255 及十進位的 -128 到 +127。 /J 編譯器選項會將預設值從變更 **`signed`** 為 **`unsigned`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[基本類型的儲存](../c-language/storage-of-basic-types.md)

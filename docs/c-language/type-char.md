---
title: 類型 char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152205"
---
# <a name="type-char"></a>類型 char

`char` 類型可用來儲存可顯示字元集之成員的整數值。 該整數值是對應所指定字元的 ASCII 碼。

**Microsoft 專屬**

`unsigned char` 類型的字元值範圍是十六進位的 0 到 0xFF。 **signed char** 的範圍是 0x80 到 0x7F。 這些範圍會分別轉譯為十進位的 0 到 255 及十進位的 -128 到 +127。 /J 編譯器選項將預設值從 **signed** 變更為 `unsigned`。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[基本類型的儲存體](../c-language/storage-of-basic-types.md)

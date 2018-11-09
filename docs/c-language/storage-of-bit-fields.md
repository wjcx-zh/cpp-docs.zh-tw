---
title: 位元欄位的儲存
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 7aa6e02c347ff14bb0552320567b343c7215ebc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499082"
---
# <a name="storage-of-bit-fields"></a>位元欄位的儲存

**ANSI 3.5.2.1**：在 int 內位元欄位的配置順序

位元欄位是在整數內依最小顯著性到最高有效位元的順序配置。 在下列程式碼中

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

位元排列如下：

```
00000001 11110010
cccccccb bbbbaaaa
```

由於 80x86 處理器會將整數值的低位元組儲存在高位元組之前，因此上面的整數 0x01F2 會在實體記憶體中儲存為 0xF2，後面接著 0x01。

## <a name="see-also"></a>請參閱

[結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)
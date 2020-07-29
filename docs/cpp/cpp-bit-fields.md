---
title: C++ 位元欄位
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 7c2dbb6e2932265984c8cb4e1e34504921e5d666
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221779"
---
# <a name="c-bit-fields"></a>C++ 位元欄位

類別和結構可包含比整數類型佔用較少儲存區的成員。 這些成員指定為位元欄位。 位欄位*成員*宣告子規格的語法如下：

## <a name="syntax"></a>語法

*declarator*宣告子 **：** *常數運算式*

## <a name="remarks"></a>備註

（*選擇性）宣告*子是在程式中用來存取成員的名稱。 它必須是整數類資料類型 (包括列舉類型)。 *常數運算式*會指定成員在結構中佔用的位數。 匿名位元欄位 (亦即沒有識別項的位元欄位成員) 可用於填補。

> [!NOTE]
> 未命名的位欄位寬度0會強制將下一個位欄位對齊下一個**類型**界限，其中**type**是成員的類型。

下列範例宣告包含位元欄位的結構：

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

`Date` 類型物件的概念性記憶體配置如下圖所示。

![Date 物件的記憶體配置](../cpp/media/vc38uq1.png "Date 物件的記憶體配置") <br/>
Date 物件的記憶體配置

請注意， `nYear` 為8位長，且會溢位已宣告類型的文字界限 **`unsigned short`** 。 因此，它會在新的開頭開始 **`unsigned short`** 。 不需要所有位元欄位都調整至基礎類型的一個物件中；新的單位儲存根據宣告所要求的位元數目進行配置。

**Microsoft 特定的**

宣告為位元欄位的資料之順序是由低至高位元，如上面的圖所示。

**結束 Microsoft 專有**

如果結構的宣告包含未命名且長度為 0 的欄位，如下列範例所示：

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

之後，記憶體配置如下圖所示：

![具有零&#45;長度位欄位的 Date 物件版面配置](../cpp/media/vc38uq2.png "具有零&#45;長度位欄位的 Date 物件版面配置") <br/>
具有長度為零之位元欄位的 Date 物件配置

位欄位的基礎類型必須是整數類資料類型，如內[建類型](../cpp/fundamental-types-cpp.md)中所述。

如果類型之參考的初始化運算式 `const T&` 是參考型別之位欄位的左值 `T` ，則參考不會直接系結至位欄位。 相反地，參考會系結至已初始化的暫存，以保存位欄位的值。

## <a name="restrictions-on-bit-fields"></a>位元欄位的限制

下列清單詳細說明位元欄位的錯誤作業：

- 取得位元欄位的位址。

- 初始化 **`const`** 具有位欄位的非參考。

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)

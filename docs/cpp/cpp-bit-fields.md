---
title: C + + 位元欄位 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69411a727c3f590e9a45a46ecb4ea2eb0eab05c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029464"
---
# <a name="c-bit-fields"></a>C++ 位元欄位

類別和結構可包含比整數類型佔用較少儲存區的成員。 這些成員指定為位元欄位。 位元欄位的語法*成員宣告子*規格如下所示：

## <a name="syntax"></a>語法

*宣告子* **:** *常數運算式*

## <a name="remarks"></a>備註

（選擇性）*宣告子*是用來存取成員的程式中的名稱。 它必須是整數類資料類型 (包括列舉類型)。 *常數運算式*結構中指定的成員所佔用的位元數。 匿名位元欄位 (亦即沒有識別項的位元欄位成員) 可用於填補。

> [!NOTE]
> 寬度 0 未命名的位元欄位強制對齊的下一個位元欄位到下一個**型別**界限，其中**型別**是成員的型別。

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

![Date 物件的記憶體配置](../cpp/media/vc38uq1.png "vc38UQ1")的 Date 物件的記憶體配置

請注意，`nYear`為 8 位元，並會溢位的宣告類型的字邊界**不帶正負號****簡短**。 因此，它新的開頭處開始**不帶正負號****簡短**。 不需要所有位元欄位都調整至基礎類型的一個物件中；新的單位儲存根據宣告所要求的位元數目進行配置。

**Microsoft 專屬**

宣告為位元欄位的資料之順序是由低至高位元，如上面的圖所示。

**結束 Microsoft 專屬**

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

記憶體配置則在下圖所示：

![具有零的 Date 物件配置&#45;長度位元欄位](../cpp/media/vc38uq2.png "vc38UQ2") Date 物件的版面配置具有長度為零的位元欄位

位元欄位的基礎類型必須是整數類型，如中所述[基本類型](../cpp/fundamental-types-cpp.md)。

如果類型參考的初始設定式`const T&`是左值參考類型的位元欄位`T`，參考未繫結至位元欄位直接。 相反地，參考繫結至初始化為值的位元欄位的暫存資料表。

## <a name="restrictions-on-bit-fields"></a>位元欄位的限制

下列清單詳細說明位元欄位的錯誤作業：

- 取得位元欄位的位址。

- 初始化非**const**具有位元欄位的參考。

## <a name="see-also"></a>另請參閱

[類別和結構](../cpp/classes-and-structs-cpp.md)
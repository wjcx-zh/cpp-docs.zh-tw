---
title: 為您的自訂類別多載 &lt;&lt; 運算子 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef542a20284d0b69d44f1092a1f311a16b999a4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>為您的自訂類別多載 &lt;&lt; 運算子

輸出資料流針對標準類型使用插入 (`<<`) 運算子。 您也可以為您的自訂類別多載 `<<` 運算子。

## <a name="example"></a>範例

`write` 函式範例示範 `Date` 結構的用法。 日期是 C++ 類別的理想候選，其中的資料成員 (月、日和年) 會隱藏不顯示。 輸出資料流是顯示這種結構的邏輯目的地。 以下程式碼使用 `cout` 物件顯示日期：

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

若要讓 `cout` 可以在插入運算子之後接受 `Date` 物件，必須多載插入運算子以識別左邊的 `ostream` 物件和右邊的 `Date`。 多載的 `<<` 運算子函式必須接著宣告為 `Date` 類別的 friend，如此它就可以存取 `Date` 物件中的私用資料。

```cpp
// overload_date.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Date
{
    int mo, da, yr;
public:
    Date(int m, int d, int y)
    {
        mo = m; da = d; yr = y;
    }
    friend ostream& operator<<(ostream& os, const Date& dt);
};

ostream& operator<<(ostream& os, const Date& dt)
{
    os << dt.mo << '/' << dt.da << '/' << dt.yr;
    return os;
}

int main()
{
    Date dt(5, 6, 92);
    cout << dt;
}
```

```Output
5/6/92
```

## <a name="remarks"></a>備註

多載的運算子會傳回原始 `ostream` 物件的參考，這表示您可以合併插入：

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>另請參閱

[輸出資料流](../standard-library/output-streams.md)<br/>

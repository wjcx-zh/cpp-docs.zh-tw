---
title: 為您的自訂類別多載 &gt;&gt; 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 86b8af963345c8eb9b3f44cfb16332bc09420bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370719"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>為您的自訂類別多載 &gt;&gt; 運算子

輸入資料流針對標準類型使用擷取 (`>>`) 運算子。 您可以為您的類別撰寫類似的擷取運算子；成功關鍵取決於是否精確地使用空白字元。

以下是稍早提供的 `Date` 類別擷取運算子範例：

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>另請參閱

[輸入資料流](../standard-library/input-streams.md)<br/>

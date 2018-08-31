---
title: 演算法 （現代 c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 604b58f7f8f6074c16effa3220d17bc00c44f5b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214310"
---
# <a name="algorithms-modern-c"></a>演算法 (現代 C++)

對於現代 c + + 程式設計，我們建議您使用中的演算法[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。 以下是一些重要的範例：

- **for_each**，這是預設周遊演算法。 (而且**轉換**不是非原地語意。)

- **find_if**，這是預設搜尋演算法。

- **排序**， **lower_bound**，和其他預設排序及搜尋演算法。

若要寫入比較子，請使用嚴格**<** 並用*具名 lambda*盡可能。

```cpp  
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );  
```

## <a name="loops"></a>迴圈

可能的話，請使用範圍型**針對**迴圈或演算法呼叫或兩者，而不是手寫的迴圈。 **複製**，**轉換**， **count_if**， **remove_if**，和其他類似項目會比手寫迴圈更好的因為其意圖很明顯，而且它們讓您更輕鬆地撰寫無 bug 的程式碼。 此外，許多 c + + 標準程式庫演算法有實作最佳化，因此更有效率。

而不是像這樣的舊 c + +:

```cpp  
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */  
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;  
}  
```

使用像這樣的現代 c + +:

```cpp  
for_each( begin(strings), end(strings), [](string& s) {
  // ...  
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```

### <a name="range-based-for-loops"></a>範圍架構的 for 迴圈

以範圍為基礎**針對**迴圈是 C + + 11 語言功能，而不是 c + + 標準程式庫演算法。 但是，有必要需迴圈在此討論中的提及。 範圍架構**for**迴圈是的延伸模組**的**關鍵字並提供便利且有效率的方式，來逐一查看值範圍的迴圈重複寫入。 C + + 標準程式庫容器、 字串和陣列是現成可供範圍架構**針對**迴圈。 若要啟用您的使用者定義型別，這個新的反覆項目語法，加入下列支援：

- A`begin`方法會傳回迭代器至結構開頭和`end`傳回迭代器至結構結尾的方法。

- 在這些方法的迭代器的支援：**運算子**<strong>\*</strong>，**運算子 ！ =**，並**operator + +** （前置版本）。

這些方法可以是成員或獨立函式。

## <a name="random-numbers"></a>隨機數字

大家，舊的 CRT`rand()`函式已有已長時間的討論中 c + + 社群中的許多缺點。 在現代 c + + 中，您不需要處理這些缺點，也不必發明自己統一分佈亂數產生器，因為中所示的工具，快速且輕鬆地建立這些c++標準程式庫，可用[\<隨機 >](../standard-library/random.md)。

## <a name="see-also"></a>另請參閱

[歡迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)<br/>

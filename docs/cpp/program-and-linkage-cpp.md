---
title: 程式和連結 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dba8698461636e292771fc1e5a4f5ac0a633e73
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238665"
---
# <a name="program-and-linkage-c"></a>程式和連結 (C++)

在 c + + 程式中，*符號*，例如變數或函式的名稱，可以宣告任何數目的時間，其在範圍內，但它一次只能定義。 這是一個定義規則 (ODR)。 A*宣告*導入了 （或重新導入了） 到程式的名稱。 A*定義*引進一個名稱，並在變數中，明確地將它初始化。 A*函式定義*簽章加上函式主體所組成。

以下是宣告：

```cpp
int i;
int f(int x);
```

這些是定義：

```cpp
int i{42};
int f(int x){ return x * i; }
```

程式包含一個或多個*轉譯單位*。 在轉譯單位是由實作檔 （.cpp、.cxx 等） 和所有標頭 （.h、.hpp 等），其中包含直接或間接所組成。 每一個轉譯單位分開編譯的編譯器之後, 連結器將編譯的轉譯單位合併成單一*程式*。 ODR 規則的違規情形通常顯示為連結器錯誤時相同的名稱不同轉譯單位中有兩個不同的定義。

一般情況下，若要跨多個檔案顯示變數的最佳方式是將其放在標頭檔，並加入 #include 指示詞需要宣告每個.cpp 檔案中。 藉由新增*include 防護*周圍的標頭內容，您確定，它會宣告的名稱只能定義一次。

不過，在某些情況下它可能需要宣告全域變數或.cpp 檔案中的類別。 在這些情況下，您需要能夠告訴編譯器和連結器物件的名稱是否適用於只一個檔案，或所有檔案。

## <a name="linkage-vs-scope"></a>與範圍的連結

概念*連結*跨轉譯單位是指全域符號 （例如變數、 型別名稱和函式名稱），在程式內的整體的可見性。 概念*範圍*指區塊，例如命名空間、 類別或函式主體內宣告的符號。 這類符號會在其所在的定義; 範圍內才可見連結的概念不適用於它們。 

## <a name="external-vs-internal-linkage"></a>外部與內部連結

A*釋放函式*的函式的定義位於全域或命名空間範圍。 非 const 全域變數和預設的可用函式具有*外部連結*; 它們會顯示在程式中的任何轉譯單位中。 因此，沒有其他全域物件 （變數、 類別定義等） 可以具有該名稱。 使用的符號*內部連結*或*沒有連結*只有在宣告它的轉譯單位內才可見。 當名稱具有內部連結時，相同的名稱可能存在其他轉譯單位中。 使用類別定義宣告變數或函式主體都不具有連結。 

您可以強制藉由明確宣告為具有內部連結的全域名稱**靜態**。 這會限制對相同轉譯單位會宣告其可見性。 請注意，在此情況下，**靜態**意義有些不同時套用至區域變數。

下列物件依預設，具有內部連結：
- const 物件
- constexpr 物件
- typedefs
- 命名空間範圍中的靜態物件

若要讓常數的物件外部連結，將它宣告為**extern**並將它指派一個值：

```cpp
extern const int value = 42;
```

請參閱[extern](extern-cpp.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

 [基本概念](../cpp/basic-concepts-cpp.md)
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
ms.openlocfilehash: 4154f0951b46b1c8badc0224845d2881cc8ad573
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="program-and-linkage--c"></a>程式和連結 （c + +）

在 c + + 程式中，即使程式包含了多個轉譯單位，則可以一次，定義每個全域符號。 在轉譯單位是由實作檔 （.cpp、.hpp、.cxx 等） 和它包含直接或間接的所有標頭所組成。 程式是由一個或多個連結在一起的轉譯單位所構成。 

## <a name="linkage-vs-scope"></a>與範圍的連結

概念*連結*跨轉譯單位是指全域符號 （例如變數、 型別名稱和函式名稱），在程式內的整體的可見性。 概念*範圍*指區塊，例如命名空間、 類別或函式主體內宣告的符號。 這類符號會在其所在的定義; 範圍內才可見連結的概念不適用於它們。

## <a name="external-vs-internal-linkage"></a>外部與內部連結

非 const 全域變數和預設受限的函式具有外部連結。它們會顯示在程式中的任何轉譯單位中。 您可以覆寫這個行為的明確宣告其作為**靜態**其限制為相同的轉譯單位在宣告其可見性。 此意義**靜態**不同於其意義，套用至區域變數。 變數宣告為**const**根據預設，具有內部連結。

## <a name="extern-constexpr-linkage"></a>外部 constexpr 連結

在舊版的 Visual Studio 中，編譯器一律會讓 constexpr 變數內部連結即使標示為 extern 變數。 在 Visual Studio 2017 15.5 版中，新編譯器參數 (/Zc:externConstexpr) 啟用正確且符合標準的行為。 這最後終究會成為預設值。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果標頭檔包含變數的宣告的 extern constexpr，應標記為 **__declspec （selectany)** 才能正確地結合其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="see-also"></a>另請參閱

 [基本概念](../cpp/basic-concepts-cpp.md)
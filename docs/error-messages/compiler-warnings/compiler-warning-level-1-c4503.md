---
title: 編譯器警告 （層級 1） C4503 |Microsoft 文件
ms.custom: ''
ms.date: 05/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60fdb44c5368ccc5c5f089002614332d95a63fe
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-warning-level-1-c4503"></a>編譯器警告 (層級 1) C4503

> '*識別碼*': 裝飾名稱長度超出範圍，名稱已遭截斷

## <a name="remarks"></a>備註

此編譯器警告已經過時，不會在 Visual Studio 2017 和更新版本的編譯器產生。

裝飾的名稱長度超過編譯器限制 (4096)，而且已被截斷。 若要避免這個警告，而且截斷，減少的引數或使用的識別項的名稱長度。 裝飾名稱超過編譯器限制都有套用雜湊，且不處於擔心名稱衝突。

當您的程式碼包含範本時使用較舊版本的 Visual Studio，可以發出這個警告重複特製化的範本。 例如，對應 （從 c + + 標準程式庫） 的對應。 在此情況下，您可以讓您 typedef 類型 (**結構**，例如)，其中包含地圖。

不過，您可能會決定不重建您的程式碼。  很可能會產生 C4503 的應用程式，但如果您在截斷的符號連結時間時發生錯誤，可能很難判斷錯誤的符號類型。 偵錯可能也會比較困難;偵錯工具可能會有困難的符號名稱對應到型別名稱。 正確性的程式，不過，不會受到截斷的名稱。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2017 之前的編譯器產生 C4503:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

這個範例會示範一種方式重寫程式碼，若要解決 C4503:

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```
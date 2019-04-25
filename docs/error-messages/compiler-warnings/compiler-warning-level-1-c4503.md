---
title: 編譯器警告 (層級 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160974"
---
# <a name="compiler-warning-level-1-c4503"></a>編譯器警告 (層級 1) C4503

> '*識別碼*': 裝飾名稱的長度超出範圍，名稱已截斷

## <a name="remarks"></a>備註

此編譯器警告已過時，而且不會在 Visual Studio 2017 和更新版本的編譯器產生。

裝飾的名稱長度超過編譯器限制 (4096)，而且已被截斷。 若要避免這個警告，而且截斷，減少的引數或使用的識別項的名稱長度。 裝飾名稱是超過編譯器限制已套用的雜湊，且不處於產生名稱衝突的風險。

當您的程式碼包含範本時使用較舊版本的 Visual Studio，可以發出這個警告的特製化範本重複。 例如，對應的對應 (從C++標準程式庫)。 在此情況下，您可以建立您 typedef 類型 (**結構**，例如)，其中包含地圖。

不過，您可能會決定不重建您的程式碼。  可提供產生 C4503 的應用程式，但如果您的已截斷的符號連結時間時發生錯誤，很難判斷錯誤的符號類型。 偵錯可能也會比較困難;偵錯工具可能無法對應至型別名稱的符號名稱。 正確性的程式，不過，不會受到截斷的名稱。

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

此範例會示範一種方法重寫您的程式碼，若要解決 C4503:

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
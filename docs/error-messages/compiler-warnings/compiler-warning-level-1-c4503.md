---
title: 編譯器警告 (層級 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 9077c448f3b5f1d70d18047b91dcf300e606c91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186540"
---
# <a name="compiler-warning-level-1-c4503"></a>編譯器警告 (層級 1) C4503

> '*identifier*'：已超過裝飾名稱長度，名稱已被截斷

## <a name="remarks"></a>備註

這個編譯器警告已過時，不會在 Visual Studio 2017 和更新版本的編譯器中產生。

裝飾名稱的長度超過編譯器限制（4096），且已截斷。 若要避免這個警告和截斷，請減少引數的數目或所使用之識別碼的名稱長度。 超過編譯器限制的裝飾名稱會套用雜湊，而不是名稱衝突的危險。

使用舊版的 Visual Studio 時，當您的程式碼包含重複用於範本的範本時，就會發出此警告。 例如，對應的對應（來自C++標準程式庫）。 在此情況下，您可以將 typedef 設為包含對應的類型（例如**結構**）。

不過，您可能會決定不要重新組織程式碼。  您可以傳送產生 C4503 的應用程式，但如果您在截斷的符號上收到連結時間錯誤，在錯誤中判斷符號的類型會比較難以。 可能也比較不容易進行調試;偵錯工具可能會無法處理將符號名稱對應至類型名稱。 不過，程式的正確性不會受到截斷的名稱所影響。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2017 之前，在編譯器中產生 C4503：

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

這個範例會示範重寫程式碼以解析 C4503 的一種方式：

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

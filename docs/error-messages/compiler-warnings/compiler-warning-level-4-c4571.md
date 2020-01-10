---
title: 編譯器警告 (層級 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990666"
---
# <a name="compiler-warning-level-4-c4571"></a>編譯器警告 (層級 4) C4571

資訊： catch （...）自 Visual C++ 7.1 後已變更的語法;已不再攔截結構化例外狀況（SEH）

使用 **/ehs**編譯時，會針對每個 catch （...）區塊產生 C4571。

使用 **/ehs**進行編譯時，catch （...）區塊不會攔截結構化例外狀況（例如零除、null 指標）;catch （...）區塊只會攔截明確擲回的C++例外狀況。  如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。

此警告預設為關閉。  開啟此警告以確保當您使用 **/ehs**編譯時，您的 catch （...）區塊不想要攔截結構化例外狀況。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

您可以利用下列其中一種方式來解析 C4571，

- 如果您仍然想要 catch （...）區塊來攔截結構化例外狀況，請使用 **/eha**進行編譯。

- 如果您不想讓 catch （...）區塊攔截結構化例外狀況，但仍想要使用 catch （...）區塊，請不要啟用 C4571。  您仍然可以使用結構化例外狀況處理關鍵字（ **__try**、 **__except**和 **__finally**）來攔截結構化例外狀況。  但請記住，編譯的C++ /ehs 析構函數只會在擲回例外狀況時呼叫，而不是在發生 SEH 例外狀況時呼叫。

- 將 catch （...）區塊C++取代為特定例外狀況的 catch 區塊，並選擇性地在C++例外狀況處理（ **__try**、 **__except**和 **__finally**）上加入結構化例外狀況處理。  如需詳細資訊，請參閱[結構化例外狀況C++處理（C/）](../../cpp/structured-exception-handling-c-cpp.md) 。

如需詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md) 。

## <a name="example"></a>範例

下列範例會產生 C4571。

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```

---
title: 編譯器警告 (層級 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 92164bf297a44871897b6c6150eb54f8c5ccf3cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220451"
---
# <a name="compiler-warning-level-4-c4571"></a>編譯器警告 (層級 4) C4571

告知性： catch 語意變更自 Visual C++ 7.1;不再攔截結構化例外狀況 (SEH)

進行編譯時，將會產生每個 catch 區塊的 C4571 **/EHs**。

進行編譯時 **/EHs**，catch 區塊不會攔截結構化的例外狀況 （除以零或 null 指標，例如）; 在 catch 區塊只會攔截明確-擲回C++例外狀況。  如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。

此警告預設為關閉。  開啟這個警告在您使用編譯時，確保 **/EHs** catch （...） 區塊不想要攔截結構化例外狀況。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

您可以在下列方面，來解決 C4571

- 使用編譯 **/EHa**若您仍想您的 catch 區塊來攔截結構化例外狀況。

- 如果不想讓您的 catch 區塊來攔截結構化例外狀況，但您仍想要使用 catch 區塊，請不要啟用 C4571。  您仍然可以攔截使用結構化例外狀況處理關鍵字的結構化例外狀況 (**__try**， **__except**，並 **__finally**)。  但是請記住，當編譯 **/EHs**解構函式只時將會呼叫C++例外狀況是，未發生時擲回 SEH 例外狀況。

- 取代特定的 catch 區塊中的 catch 區塊C++例外狀況，並選擇性地將結構化的例外處理周圍C++例外狀況處理 (**__try**， **__except**，和 **__finally**)。  請參閱[Structured Exception Handling (C /C++)](../../cpp/structured-exception-handling-c-cpp.md)如需詳細資訊。

請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C4571。

```
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
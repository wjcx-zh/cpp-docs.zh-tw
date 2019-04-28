---
title: 編譯器警告 (層級 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349681"
---
# <a name="compiler-warning-level-2-c4275"></a>編譯器警告 (層級 2) C4275

> 非 DLL 介面的類別*class_1*'做為基底 DLL 介面類別'*class_2*'

匯出的類別衍生自不匯出的類別。

若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確定：

- 所有靜態資料是透過從 DLL 匯出的函式存取。

- 沒有內嵌的方法，您的類別可以修改靜態資料。

- 沒有內嵌的方法，您的類別使用 CRT 函式或使用靜態資料的其他程式庫函式。

- 沒有內嵌的類別函式會使用 CRT 函式或其他程式庫函式中，您用來存取靜態資料。

- 您的類別沒有任何方法 (不管內嵌) 可以用來使用 EXE 和 DLL 中的具現化其中有靜態資料差異的類型。

您可以避免匯出類別所定義的 DLL，定義具有虛擬函式，類別和函式您可以呼叫來具現化和刪除的物件類型。  然後，您就可以再呼叫虛擬函式類型。

視覺效果中，您可以忽略 C4275C++如果您衍生自中的型別C++標準程式庫、 編譯偵錯版本 (**/MTd**) 和編譯器錯誤訊息會指`_Container_base`。

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```